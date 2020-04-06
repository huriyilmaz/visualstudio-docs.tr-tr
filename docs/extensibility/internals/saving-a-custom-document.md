---
title: Özel Belge Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705608"
---
# <a name="saving-a-custom-document"></a>Özel Belge Kaydetme
Ortam **Kaydet,** **Farklı Kaydet**ve Tüm komutları **kaydet** işlemlerini işler. Bir kullanıcı **Dosya** menüsünde **Kaydet**, **Kaydet** **veya Tümlerini Kaydet** menüsünde tıklattığında veya çözümü kapattığında ve tümleri kaydet işlemiyle sonuçlanırsa, aşağıdaki işlem gerçekleşir.

 ![Müşteri Editörü Kaydet](../../extensibility/internals/media/private.gif "Özel") Özel bir düzenleyici için Tüm komut işlemeyi kaydet, Kaydet ve Kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak açıklanır:

1. Farklı **Kaydet** ve **Kaydet** komutları <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> için ortam, etkin belge penceresini belirlemek için hizmeti kullanır ve böylece hangi öğelerin kaydedilmesi gerektiğini belirler. Etkin belge penceresi bilindikten sonra, ortam çalışan belge tablosundaki belgeiçin hiyerarşi işaretçisini ve öğe tanımlayıcısını (itemID) bulur. Daha fazla bilgi için [Bkz. Belge Tablosunu Çalıştır.](../../extensibility/internals/running-document-table.md)

     Tümöğeleri Kaydet komutu için ortam, kaydetmek için tüm öğelerin listesini derlemek için çalışan belge tablosundaki bilgileri kullanır.

2. Çözüm bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrı aldığında, seçili öğeler kümesi (diğer bir <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> şekilde, hizmet tarafından ortaya çıkarılan birden çok seçim) ile yinelenir.

3. Seçimdeki her öğede çözüm, Kaydet menüsü komutu etkin olup olmadığını belirlemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> yöntemi çağırmak için hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirliyse, Kaydet komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> yöntem çağırarak kirli durum için sorgulayan hiyerarşi temsilcileri düzenleyiciye bildirir.

4. Kirli olan her seçili öğede çözüm, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> yöntemi uygun hiyerarşilerde çağırmak için hiyerarşi işaretçisini kullanır.

     Özel bir düzenleyici söz konusu olduğunda, belge veri nesnesi ile proje arasındaki iletişim özeldir. Böylece, herhangi bir özel kalıcılık endişeleri bu iki nesne arasında ele alınır.

    > [!NOTE]
    > Kendi kalıcılığınızı uygularsanız, zamandan tasarruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> etmek için yöntemi aradığınızdan emin olun. Bu yöntem, dosyayı kaydetmenin güvenli olduğundan emin olmak için denetler (örneğin, dosya salt okunur değil).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
