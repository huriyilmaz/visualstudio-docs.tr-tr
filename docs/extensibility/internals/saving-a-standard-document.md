---
title: Standart Belge | Microsoft Docs
description: IDE'ye ek olarak proje türü için standart bir belge için oluşan işlem hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71e4aaa99a17e8643af104a30e12caf3300e0570a00cc1715d80016333aff64f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375668"
---
# <a name="saving-a-standard-document"></a>Standart Belge Kaydetme
Ortam Kaydet, Farklı Kaydet ve Tüm Komutları Kaydet komutlarını işler. Bir kullanıcı Dosya **menüsünden Kaydet,** **Farklı** Kaydet  veya Hepsini Kaydet'i seçerek çözümü kapatarak Hepsini Kaydet'i seçerek aşağıdaki işlem gerçekleşir. 

 ![Standart Düzenleyici](../../extensibility/internals/media/public.gif "Genel") Standart düzenleyici için Kaydet, Farklı Kaydet ve Tüm komut işlemeyi kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak açıktır:

1. Farklı **Kaydet** ve **Farklı Kaydet** komutları seçildiğinde ortam, etkin belge penceresini ve bu nedenle hangi öğelerin kaydedileceklerini belirlemek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti kullanır. Etkin belge penceresi bilindiği zaman ortam, çalışan belge tablosunda belgenin hiyerarşi işaretçisini ve öğe tanımlayıcısını (itemID) bulur. Daha fazla bilgi için [bkz. Belge Tablosu Çalıştırma.](../../extensibility/internals/running-document-table.md)

    Tüm **Öğeleri Kaydet** komutu seçildiğinde ortam, kaydedilecek tüm öğelerin listesini derlemek için çalışan belge tablosunda yer alan bilgileri kullanır.

2. Çözüm bir çağrı aldığında, seçilen öğe kümesinde (yani hizmet tarafından ortaya çıkarıla birden çok <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> seçim) aynı şekilde <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> devam eder.

3. Seçimde yer alan her öğede çözüm, Kaydet menü komutunun etkin olup olmadığını belirlemek üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> **yöntemini çağıran hiyerarşi** işaretçisini kullanır. Bir veya daha fazla öğe kirli ise Kaydet **komutu** etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, hiyerarşi yöntemini çağırarak kirli durum sorgulamayı düzenleyiciye <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> devreder.

4. Kirli olan her seçili öğede çözüm, uygun hiyerarşilerde yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> çağıran hiyerarşi işaretçisini kullanır.

    Hiyerarşide belgeyi düzenlemek için standart bir düzenleyici kullanmak yaygındır. Bu durumda, bu düzenleyicinin belge veri nesnesi arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> desteklemeli. Yöntem çağrısını aldıktan sonra proje, belge veri nesnesinde yöntemini çağırarak belgenin kayded olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> düzenleyiciye bildirmeli. Düzenleyici, arabirimini çağırarak ortamın **Farklı Kaydet** iletişim kutusunu `Query Service` işlemesine olanak <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> sağlar. Bu, arabirimin işaretçisini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> döndürür. Düzenleyicinin daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> yöntemini çağırarak parametresiyle düzenleyicinin uygulamasına <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> bir işaretçi geçirmesi `pPersistFile` gerekir. Ortam daha sonra Kaydet işlemini gerçekleştirir ve düzenleyici **için Farklı** Kaydet iletişim kutusunu sağlar. Ortam daha sonra ile düzenleyiciye geri <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> çağrır.

5. Kullanıcı adsız bir belgeyi (daha önce kaydedlanmamış bir belge) kaydetmeye çalışırken, aslında bir Farklı Kaydet komutu gerçekleştirilir.

6. Farklı Kaydet komutu için, ortam Farklı Kaydet iletişim kutusunu görüntüler ve kullanıcıdan bir dosya adı istemi görüntüler.

    Dosyanın adı değiştiyse, hiyerarşi çağrılarak belge çerçevesinin önbelleğe alınmış bilgilerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> güncelleştirmekten (VSFPROPID_MkDocument).

   Farklı **Kaydet komutu** belgenin konumunu taşırsa ve hiyerarşi belge konumu için hassassa, açık belge penceresinin sahipliğini başka bir hiyerarşiye teslim etmek hiyerarşinin sorumluluğundadır. Örneğin, proje, dosyanın projeyle ilgili olarak bir iç veya dış dosya (Çeşitli Dosya) olup olmadığını izlerse bu durum oluşur. Bir dosyanın sahipliğini Çeşitli Dosyalar projesine değiştirmek için aşağıdaki yordamı kullanın.

## <a name="changing-file-ownership"></a>Dosya Sahipliğini Değiştirme

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Dosya sahipliğini Çeşitli Dosyalar projesine değiştirmek için

1. Arabirim için Sorgu <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> Hizmeti.

     işaretçisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> döndürülür.

2. Belgeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> yeni `pszMkDocumentNew` `punkWindowFrame` hiyerarşiye aktaran ( , ) yöntemini çağırma. Farklı Kaydet komutunu gerçekleştiren hiyerarşi bu yöntemi çağırıyor.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
