---
title: Standart Belge kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705547"
---
# <a name="saving-a-standard-document"></a>Standart Belge Kaydetme
Ortam, Tümeği Kaydet, Kaydet ve Tüm komutları kaydet işlemlerini işler. Bir kullanıcı **Dosya** menüsünden **Kaydet**, **Kaydet**veya **Tümünü Kaydet** seçeneğini seçtiğinde veya çözümü kapattığında, **tümünü kaydet**işlemi yle sonuçlanır, aşağıdaki işlem gerçekleşir.

 ![Standart Editör](../../extensibility/internals/media/public.gif "Genel") Standart bir düzenleyici için Tüm komut işlemeyi kaydet, Kaydet ve Kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak açıklanır:

1. Farklı **Kaydet** ve **Kaydet** komutları seçildiğinde, ortam etkin belge penceresini belirlemek ve böylece hangi öğelerin kaydedilmesi gerektiğini belirlemek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti kullanır. Etkin belge penceresi bilindikten sonra, ortam çalışan belge tablosundaki belgeiçin hiyerarşi işaretçisini ve öğe tanımlayıcısını (itemID) bulur. Daha fazla bilgi için [Bkz. Belge Tablosunu Çalıştır.](../../extensibility/internals/running-document-table.md)

    **Tümöğeleri Kaydet** komutu seçildiğinde, ortam, kaydetmek için tüm öğelerin listesini derlemek için çalışan belge tablosundaki bilgileri kullanır.

2. Çözüm bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrı aldığında, seçili öğeler kümesi (diğer bir <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> şekilde, hizmet tarafından ortaya çıkarılan birden çok seçim) ile yinelenir.

3. Seçimdeki her öğede çözüm, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> **Kaydet** menüsü komutu etkin olup olmadığını belirlemek için yöntemi çağırmak için hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirliyse, **Kaydet** komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> yöntem çağırarak kirli durum için sorgulayan hiyerarşi temsilcileri düzenleyiciye bildirir.

4. Kirli olan her seçili öğede çözüm, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> yöntemi uygun hiyerarşilerde çağırmak için hiyerarşi işaretçisini kullanır.

    Hiyerarşinin belgeyi yeniden biçimlendirecek standart bir düzenleyici kullanması yaygındır. Bu durumda, bu düzenleyici için belge veri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> nesnesi arabirimi desteklemesi gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Yöntem çağrısını aldıktan sonra, proje, belge veri nesnesi üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> yöntem çağırArak belgenin kaydedildiğini düzenleyiciye bildirmelidir. Düzenleyici, arabirimi arayarak `Query Service` ortamın **Farklı Kaydet** iletişim <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> kutusunu işlemesine izin verebilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Bu, arabirime bir işaretçi döndürür. Editör daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> `pPersistFile` parametre ile editörün uygulamasına bir işaretçi geçirerek yöntemi çağırmalıdır. Ortam daha sonra Kaydet işlemini gerçekleştirir ve düzenleyici için **Farklı Kaydet** iletişim kutusunu sağlar. Ortam daha sonra editöre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>geri çağırır.

5. Kullanıcı adsız bir belgeyi (diğer bir şekilde, önceden kaydedilmemiş bir belge) kaydetmeye çalışıyorsa, Gerçekte Bir Farklı Kaydet komutu gerçekleştirilir.

6. Farklı Kaydet komutu için ortam, Kullanıcı'yı bir dosya adı için isteyen As Olarak Kaydet iletişim kutusunu görüntüler.

    Dosyanın adı değiştiyse, hiyerarşi belge çerçevesinin önbelleğe alınmış bilgilerini arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument) güncelleştirmekten sorumludur.

   Farklı **Kaydet** komutu belgenin konumunu taşırsa ve hiyerarşi belge konumuna duyarlıysa, hiyerarşi açık belge penceresinin sahipliğini başka bir hiyerarşiye teslim etmekle yükümlüdür. Örneğin, proje, dosyanın projeyle ilgili iç veya dış dosya (Çeşitli Dosya) olup olmadığını izlerse oluşur. Bir dosyanın sahipliğini Çeşitli Dosyalar projesiyle değiştirmek için aşağıdaki yordamı kullanın.

## <a name="changing-file-ownership"></a>Dosya Sahipliğini Değiştirme

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Dosya sahipliğini Çeşitli Dosyalar projesiyle değiştirmek için

1. <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> Arabirim için Sorgu Hizmeti.

     Bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> döndürülür.

2. Belgeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew`yeni `punkWindowFrame`hiyerarşiye aktarmak için ( , ) yöntemini arayın. Farklı Kaydet komutunu gerçekleştiren hiyerarşi bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
