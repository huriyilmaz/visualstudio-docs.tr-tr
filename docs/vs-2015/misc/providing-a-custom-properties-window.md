---
title: Özel Özellikler penceresi sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810714"
---
# <a name="providing-a-custom-properties-window"></a>Özel Özellikler penceresi sağlama
Tümleşik geliştirme ortamı (IDE) tarafından sağlanan **Özellikler** penceresini genişletmek yerine, belirli bir proje sistemi Için kendi **Özellikler** pencerenizi sağlamak mümkündür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . En yaygın olarak karşılaşılan senaryo, bir nesneyi pencere çerçevesinde uygulığınızdaki bir nesnedir.  
  
 Bu durumda, nesneyi pencere çerçevesinde gerçekleştirmeyin, ancak başka bir şekilde buna hala erişebilseniz de, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Bu sayfadaki son yordamda listelenen arabirime erişmenin birkaç yolu vardır.  
  
### <a name="to-provide-your-properties-window"></a>Özellikler penceresi sağlamak için  
  
1. **Özellikler** penceresi uygulamanızı temsil eden bir GUID tanımlayın.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>Uygulamanızda, <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Visual Studio ortamına yönelik bir hizmet olarak **Özellikler** pencerenizi sağlamak için hizmetini kullanın.  
  
### <a name="to-call-your-properties-window"></a>Özellikler pencerenizi çağırmak için  
  
1. Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` ' <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> den ' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e geçirilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> yöntemine.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>Hizmetten alın <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> .  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> `SEID_PropertyBrowserSID` <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> `varValue` **Özellik** pencerenizi temsil eden GUID 'nin dize biçimini temsil eden (numaralandırmasından alınan) ve üçüncü parametresi olan ilk parametre ayarlanmış olan çağrı. Bu çağrıyı, **Özellikler** penceresi belge pencerenizi ilk oluştururken yalnızca bir kez yapın. Bu **özellikleri** çağır penceresi pencere çerçevenize ilişkiliydi.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Uygulayıcısı olmadığında pencere çerçevesi nesnesini almak için  
  
- Hizmeti için `QueryService` , <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> olarak ayarlanmış parametresi ile kullanabilirsiniz `propid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>SVsMonitorSelection hizmetini çağırarak etkin belge penceresini elde edebilirsiniz. Parametresini, `elementid` `SEID_WindowFrame` numaralandırmasından alınmış olarak ayarlayın <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri genişletme](../extensibility/internals/extending-properties.md)   
 [Özellikler Penceresi Alanları ve Arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md)