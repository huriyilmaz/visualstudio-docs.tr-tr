---
title: Standart bir belge kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724092"
---
# <a name="saving-a-standard-document"></a>Standart Belge Kaydetme
Ortam Kaydet, farklı Kaydet ve Tümünü Kaydet komutlarını işler. Kullanıcı **Kaydet**, **farklı kaydet**veya **Dosya** menüsünden **Tümünü** Kaydet ' i seçtiğinde veya çözümü kapatdığında, bir **bütün kaydetme**işlemine neden olur.

 ![Standart düzenleyici](../../extensibility/internals/media/public.gif "Ortak") Standart bir düzenleyici için Kaydet, farklı Kaydet ve tüm komut işlemesini Kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak verilmiştir:

1. **Kaydet** ve **farklı kaydet** komutları seçildiğinde, ortam, etkin belge penceresini ve bu nedenle hangi öğelerin kaydedilmesi gerektiğini belirlemek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmetini kullanır. Etkin belge penceresi bilindiğinde ortam, çalışan belge tablosundaki belge için hiyerarşi işaretçisini ve öğe tanımlayıcısını (ItemId) bulur. Daha fazla bilgi için bkz. [çalışma belge tablosu](../../extensibility/internals/running-document-table.md).

    **Tümünü Kaydet** komutu seçildiğinde, ortam, kaydedilecek tüm öğelerin listesini derlemek için çalışan belge tablosundaki bilgileri kullanır.

2. Çözüm bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrısı aldığında, seçilen öğeler kümesi (yani, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti tarafından sunulan çoklu seçimler) boyunca yinelenir.

3. Seçimdeki her öğe için çözüm, **Kaydet** menü komutunun etkinleştirilip etkinleştirilmeyeceğini anlamak üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> yöntemini çağırmak için hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirli olursa **Kaydet** komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, hiyerarşi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> yöntemini çağırarak, bu durumda, durumu düzenleyiciye için kirli durum sorgulama temsilcileri sağlar.

4. Kirli olan her seçili öğe için, çözüm uygun hiyerarşilerde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> yöntemini çağırmak için hiyerarşi işaretçisini kullanır.

    Hiyerarşinin belgeyi düzenlemek için standart bir düzenleyici kullanması yaygındır. Bu durumda, Bu düzenleyicinin belge veri nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimini desteklemelidir. @No__t_0 yöntemi çağrısını aldıktan sonra, proje, belge verileri nesnesinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodunu çağırarak düzenleyiciyi belgenin kaydedildiğini bilgilendirmelidir. Düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> arabirimi için `Query Service` çağırarak, ortamın **farklı kaydet** iletişim kutusunu işlemesine izin verebilir. Bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimine bir işaretçi döndürür. Daha sonra düzenleyici, `pPersistFile` parametresi aracılığıyla düzenleyicinin <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulamasına bir işaretçi geçirerek <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> yöntemini çağırmalıdır. Daha sonra ortam, Kaydet işlemini gerçekleştirir ve düzenleyici için **farklı kaydet** iletişim kutusunu sağlar. Daha sonra ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> ile düzenleyiciye geri çağrı yapılır.

5. Kullanıcı adsız bir belgeyi (yani, daha önce kaydedilmemiş bir belgeyi) kaydetmeye çalışıyorsa, aslında farklı Kaydet komutu gerçekleştirilir.

6. Farklı Kaydet komutu için, ortamda farklı Kaydet iletişim kutusu görüntülenir ve kullanıcıdan bir dosya adı istenir.

    Dosyanın adı değiştiyse, hiyerarşi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument) çağırarak belge çerçevesinin önbelleğe alınmış bilgilerini güncelleştirmekten sorumludur.

   **Farklı kaydet** komutu belgenin konumunu taşıdıkça ve hiyerarşi belge konumuna duyarlıysa, bu durumda açık belge penceresinin sahipliğini başka bir hiyerarşiye teslim etmek için hiyerarşi sorumludur. Örneğin, proje, dosyanın proje ile bağlantılı olarak bir iç veya dış dosya (çeşitli dosya) olup olmadığını izliyorsa bu durum oluşur. Bir dosyanın sahipliğini çeşitli dosyalar projesine değiştirmek için aşağıdaki yordamı kullanın.

## <a name="changing-file-ownership"></a>Dosya sahipliğini değiştirme

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Dosya sahipliğini çeşitli dosyalar projesiyle değiştirmek için

1. @No__t_0 arabirimi için sorgu hizmeti.

     @No__t_0 bir işaretçi döndürülür.

2. Belgeyi yeni hiyerarşiye aktarmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) metodunu çağırın. Farklı Kaydet komutunu gerçekleştiren hiyerarşi bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)