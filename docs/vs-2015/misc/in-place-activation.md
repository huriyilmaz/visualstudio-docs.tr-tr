---
title: Yerinde etkinleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802928"
---
# <a name="in-place-activation"></a>Yerinde etkinleştirme
Düzenleyiciniz görünümü ActiveX veya diğer etkin denetimleri barındırıyorsa, düzenleyici görünümünüzü bir ActiveX denetimi olarak veya etkin bir belge veri nesnesi olarak yerinde etkinleştirme modelini kullanarak uygulamanız gerekir.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Menüler, araç çubukları ve komutlar için destek  
 Visual Studio, düzenleyici görünümlerinizin IDE 'nin menülerini ve araç çubuklarını kullanmasına izin verir. Bu uzantılar, *OLE yerinde bileşenler*olarak adlandırılır. Daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> . ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> .  
  
 Bir ActiveX denetimi uygularsanız, diğer katıştırılmış nesneleri barındırabilirsiniz. Bir belge veri nesnesi uygularsanız, pencere çerçevesi, ActiveX denetimlerini kullanma yeteneğinizi kısıtlar.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>Ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> arabirimleri, verilerin ve görünümün bir ayrımı için izin verir. Ancak, Visual Studio bu işlevi desteklemez ve bu arabirimler yalnızca belge görünümü nesnesini temsil etmek için kullanılır.  
  
 Hizmeti kullanan düzenleyiciler, <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> hizmet tarafından uygulanan arabirimin yöntemlerini çağırarak menü, araç çubuğu ve komut tümleştirmesi sağlayabilir <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Düzenleyiciler, seçim izleme ve yönetimi geri alma gibi diğer Visual Studio işlevlerini de sunabilir. Daha fazla bilgi için bkz. [özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Kullanılan nesneler ve arabirimler  
 Yerinde etkinleştirme oluşturmak için kullanılan nesneler aşağıdaki çizimde gösterilmiştir.  
  
 ![&#45;yerinde etkinleştirme Düzenleyicisi](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Yerinde etkinleştirme Düzenleyicisi  
  
> [!NOTE]
> Bu çizimdeki nesnelerden yalnızca `CYourEditorFactory` nesne, standart bir düzenleyici oluşturmak için gereklidir. Özel bir düzenleyici oluşturuyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> düzenleyiciniz büyük olasılıkla kendi özel Kalıcılık mekanizmasına sahip olacağı için uygulamanız gerekmez. Daha fazla bilgi için bkz. [özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md).  
  
 Bir yerinde etkinleştirme Düzenleyicisi oluşturmak için uygulanan tüm arabirimler tek `CYourEditorDocument` nesnede gösterilir, ancak bu yapılandırma yalnızca belge verilerinin tek bir görünümünü destekler. Belge verilerinizin birden çok görünümünü destekleme hakkında daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).  
  
|Arabirim|Nesne türü|Kullanın|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Görünüm|Yerinde VSPackage nesnelerinin, hizmeti kullanarak IDE 'nin tamamen tümleşik bileşenleri olarak çalışmasını sağlar <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Bu hizmet, nesnenin menülerini, araç çubuklarını ve komutlarını IDE 'ye ve durum değişikliklerinin sorun bildirimlerini tümleştirir.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Görünüm|Asıl, gömülü bir nesnenin kapsayıcısına temel işlevsellik sağladığı ve bununla iletişim kurduğu anlamına gelir.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Görünüm|Yerinde nesnelerin etkinleştirilmesini ve devre dışı bırakılması işlemini yönetir ve yerinde nesnenin ne kadarının görünür olacağını belirler.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Görünüm|Bir yerinde nesne, ilişkili uygulamanın en dıştaki çerçevesi penceresi ve katıştırılmış nesneyi içeren uygulamadaki belge penceresi arasında doğrudan iletişim kanalı sağlar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Görünüm|Bir ActiveX nesnesi uygular. <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` Belge verilerinin ve görünümün ayrı ve bu yöntemlerinin IDE 'de kullanılmadığını unutmayın.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Görünüm/veri|Belge veri nesnesini veya belge görünümü nesnesini ya da her ikisini de komut işleme katılmasını sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Görünüm|Durum çubuğu güncelleştirmelerini etkinleştirilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Görünüm|Araç kutusuna öğe eklemeyi sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Veriler|Düzenlenen dosyadaki değişiklikler hakkında bildirim gönderir. (Bu arabirim isteğe bağlıdır.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Veriler|Dosya türü için farklı Kaydet özelliğini etkinleştirmek üzere kullanılır.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Veriler|Belge için kalıcılığı mümkün hale getirme. Salt okuma dosyaları için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> salt okuma dosyalarını belirten "kilit" simgesini sağlamak için öğesini çağırın.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Veriler|Belge verilerinde değişiklik yapılıp yapılmayacağını belirler.|