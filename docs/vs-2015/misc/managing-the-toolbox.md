---
title: Araç kutusunu yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681536"
---
# <a name="managing-the-toolbox"></a>Araç kutusunu yönetme
, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] **Araç kutusunun**üyeliğini ve görünümünü yönetmek için bir düzenleyici veya tasarımcı gibi bir VSPackage sağlar.  
  
 Ayrıca, **araç kutusu** Otomasyon kullanılarak yönetilebilir. Araç kutusunu Otomasyon aracılığıyla yönetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: araç kutusunu denetleme](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Otomatik Araç kutusu sekme seçimi  
 Belirli bir **araç kutusu** sekmesi veya kategorisi, şu anda etkin olan düzenleyici veya tasarımcı temel alınarak otomatik olarak etkin hale getirilebilir. Örneğin, bir form Tasarımcısı etkinleştirildiyse, **tüm Windows Forms** sekmesinin seçili olmasını isteyebilirsiniz.  
  
 Bu destek, gereken düzenleyicilerle ve tasarımcılarla sınırlıdır:  
  
1. Düzenleyici veya tasarımcı örnekleri sağlamak için bir fabrika nesnesinin uygulanması. Tasarımcı veya düzenleyici fabrikası nesnesi uygulama hakkında daha fazla bilgi için bkz. [Düzenleyici fabrikaları](../extensibility/editor-factories.md).  
  
2. Düzenleyici veya tasarımcı mevcutsa araç kutusu sekmesinin kaydı otomatik olarak etkinleştirilir.  
  
## <a name="controlling-the-toolbox"></a>Araç kutusunu denetleme  
 Otomasyon desteğini takıma alma, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSPackages 'In **araç kutusunun** nasıl yönetildiği üzerinde daha fazla denetim sağlamak için aşağıdaki arabirimleri sağlar.  
  
|Arabirim|Description|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Uygulamaların <xref:System.Drawing.Design.ToolboxItem> **araç kutusu**'ndan nesneleri yönetmesine, eklemesine ve kaldırmasına izin verir. Ayrıca görünüm ve **araç kutusu** kategorilerinin yapılandırılmasını da sunar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Uygulamaların etkin tabanlı **araç kutusu** denetimlerini yönetmesine, eklemesine ve kaldırmasına izin verir ve **araç kutusu** kategorilerini ve görünümünü yapılandırır.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>Kalıcılık ve yerelleştirme için kapsamlı destek sunarak içinde bulunan işlevselliği genişletir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Bu arabirimlere çalışırken göz önünde bulundurmanız gereken birkaç önemli nokta vardır:  
  
- <xref:System.Drawing.Design.IToolboxService> yalnızca yönetilen paket çerçevesi tabanlı VSPackages 'lar için kullanılabilir.  
  
- Denetimler, kullanılarak **araç kutusuna** doğrudan eklenemez <xref:System.Drawing.Design.IToolboxService> .  
  
- Bir VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> , denetim eklemek veya denetimi ' den türetilen bir sarmalayıcı denetimine barındırmak için kullanılmalıdır <xref:System.Windows.Forms.AxHost> .  
  
   Visual Studio, `Aximp.exe` ' den türetilen bir denetimdeki ActiveX denetiminin sarmalanması için araç sağlar <xref:System.Windows.Forms.AxHost> . Daha fazla bilgi için bkz. [Aximp.exe (Windows Forms ActiveX denetim Içeri Aktarıcı)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> birlikte çalışma derlemeleri aracılığıyla kullanılabilen com tabanlı arabirimlerdir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> öğesinden türetilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> ve tüm yöntemlerini uygular.  
  
   Nesneler yalnızca bir örneğini elde eder <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> , öğesinden türetilmez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve yöntemlerini uygulamaz.  
  
   Her iki arabirimde da işlevlere ihtiyaç duyan nesneler, ortamdan her iki arabirimin örneğini almalıdır.  
  
- Ve ile çalışırken <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> , sekmelerin kurallı (yerelleştirilmemiş) adları hakkında bilgi <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> ve yöntemleri tarafından işlenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> .  
  
- Kullanırken <xref:System.Drawing.Design.IToolboxService> , kategorilerin adları gibi yerelleştirilmiş bilgileri yönetmek için uygulayıcısı vardır.  
  
  Kullanıcıların, kullanıcılar tarafından erişilen **araç kutusu** AYARLARıNı, IDE 'nin **Araçlar** menüsünde bulunan **içeri/dışarı aktarma ayarları** komutundan kaydetmelerini sağlamak için ayarlar mekanizmasını kullanın. Ayarları kullanma hakkında daha fazla bilgi için bkz. [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusunu genişletme](../misc/extending-the-toolbox.md)