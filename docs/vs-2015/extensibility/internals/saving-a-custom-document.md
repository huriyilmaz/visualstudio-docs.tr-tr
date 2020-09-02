---
title: Özel bir belgeyi kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d41b075111797a12d68b4aa30c23e3cbacd8058a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64836322"
---
# <a name="saving-a-custom-document"></a>Özel Belge Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ortam **Kaydet**, **farklı kaydet**ve **Tümünü Kaydet** komutlarını işler. Kullanıcı **Kaydet**, **farklı kaydet**veya **Dosya** menüsünde **Tümünü** Kaydet ' i tıklattığında ya da çözümü kapatsa da, Tümünü Kaydet ' i tıklattığınızda aşağıdaki işlem gerçekleşir.  
  
 ![Müşteri Düzenleyicisini Kaydet](../../extensibility/internals/media/private.gif "Özel")  
Özel bir düzenleyici için Kaydet, farklı Kaydet ve tüm komut işlemesini Kaydet  
  
 Bu işlem aşağıdaki adımlarda ayrıntılı olarak verilmiştir:  
  
1. Farklı **Kaydet** ve **Kaydet** komutları için, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> etkin belge penceresini ve bu nedenle hangi öğelerin kaydedilmesi gerektiğini belirlemek için hizmetini kullanır. Etkin belge penceresi bilindiğinde ortam, çalışan belge tablosundaki belge için hiyerarşi işaretçisini ve öğe tanımlayıcısını (ItemId) bulur. Daha fazla bilgi için bkz. [çalışma belge tablosu](../../extensibility/internals/running-document-table.md).  
  
     Tümünü Kaydet komutu için, ortam, kaydedilecek tüm öğelerin listesini derlemek için çalışan belge tablosundaki bilgileri kullanır.  
  
2. Çözüm bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrı aldığında, seçilen öğeler kümesi (yani, hizmet tarafından sunulan çoklu seçimler) boyunca yinelenir <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
3. Seçimdeki her öğe için çözüm, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Kaydet menü komutunun etkinleştirilmesi gerekip gerekmediğini belirleme yöntemini çağırmak için hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirli olursa Kaydet komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, hiyerarşi, metodu çağırarak, bu durumda, durumu düzenleyicide kirli durum için sorgulama temsilcileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4. Kirli olan her seçili öğe için, çözüm uygun hiyerarşilerde yöntemi çağırmak için hiyerarşi işaretçisini kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> .  
  
     Özel bir düzenleyici söz konusu olduğunda, belge verileri nesnesi ve proje arasındaki iletişim özeldir. Bu nedenle, tüm özel Kalıcılık sorunları bu iki nesne arasında işlenir.  
  
    > [!NOTE]
    > Kendi kalıcılığını uygularsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> zaman kazanmak için yöntemini çağırdığınızdan emin olun. Bu yöntem, dosyanın kaydedilmesi güvenli olduğundan emin olmak için kontrol eder (örneğin, dosya salt okunurdur).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
