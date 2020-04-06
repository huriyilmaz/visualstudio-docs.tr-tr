---
title: 'Nasıl Yapilir: Hizmet Alın | Microsoft Dokümanlar'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710953"
---
# <a name="how-to-get-a-service"></a>Nasıl yapilir: Hizmet alın

Farklı özelliklere erişmek için sık sık Visual Studio hizmetlerine sahip olmanız gerekir. Genel olarak, Visual Studio hizmeti kullanabileceğiniz bir veya daha fazla arabirim sağlar. Çoğu hizmeti bir VSPackage'dan alabilirsiniz.

Herhangi bir VSPackage türetilmiştir <xref:Microsoft.VisualStudio.Shell.Package> ve bu doğru sited olmuştur herhangi bir küresel hizmet isteyebilirsiniz. `Package` Sınıf uygular <xref:System.IServiceProvider>çünkü, herhangi bir VSPackage türetilmiştir da bir hizmet `Package` sağlayıcısıdır.

Visual Studio a <xref:Microsoft.VisualStudio.Shell.Package>yüklendiğinde, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> başlatma <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> sırasında yönteme bir nesne geçer. Buna VSPackage'ı *sitme* denir. Sınıf `Package` bu hizmet sağlayıcısını sarar ve hizmet alma yöntemini <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> sağlar.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Parayla alınan BIR VSPackage'dan hizmet alma

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. Adlı `GetServiceExtension` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Şimdi **GetServiceCommand**adlı özel bir komut öğesi şablonu ekleyin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında, komut dosyası adını *GetServiceCommand.cs*olarak değiştirin. Özel komut oluşturma hakkında daha fazla bilgi için [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

3. *GetServiceCommand.cs,* yöntemin gövdesini `MenuItemCommand` kaldırın ve aşağıdaki kodu ekleyin:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Bu kod bir SVsActivityLog hizmeti alır <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> ve etkinlik günlüğüne yazmak için kullanılabilecek bir arabirime atar. Örneğin, [bkz.](../extensibility/how-to-use-the-activity-log.md)

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

5. Deneme örneğinin **Araçlar** menüsünde, **Invoke GetServiceCommand** düğmesini bulun. Bu düğmeyi tıklattığınızda, etkinlik günlüğü hizmetini bulduğunu belirten bir ileti kutusu görmeniz **gerekir.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Bir araç penceresinden veya kontrol konteynerinden hizmet alma

Bazen bir araç penceresinden veya sited edilmemiş bir denetim kapsayıcısından veya istediğiniz hizmet hakkında bilgi olmayan bir hizmet sağlayıcısıyla sited'den hizmet almanız gerekebilir. Örneğin, bir denetim içinden etkinlik günlüğüne yazmak isteyebilirsiniz.

Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntem, önbelleğe alınmış bir hizmet sağlayıcısına dayanır ve bu <xref:Microsoft.VisualStudio.Shell.Package> hizmet sağlayıcısı ilk kez bir VSPackage'ın türetildiği zaman başlatılan siteye dayanır.

VSPackage oluşturucu, VSPackage sited önce denir çünkü, küresel hizmetler genellikle VSPackage oluşturucu içinden kullanılamaz. Bkz. [Nasıl Olunacak:](../extensibility/how-to-troubleshoot-services.md) Geçici çözüm için hizmetleri sorun giderme.

Aşağıda, bir araç penceresinde veya VSPackage olmayan diğer bir öğede hizmet almanın bir yolu örneği verilmiştir.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE nesnesinden hizmet alma

Ayrıca nesneden <xref:EnvDTE.DTEClass> hizmet alabilirsiniz. Ancak, Bir VSPackage bir hizmet olarak veya statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi çağırarak DTE nesnesi almak gerekir.

DTE nesnesi <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>uygular , kullanarak bir hizmet için <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>sorgulamak için kullanabilirsiniz.

DTE nesnesinden hizmet nasıl alabilirsiniz.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Hizmet sağlama](../extensibility/how-to-provide-a-service.md)
- [Kullanım ve hizmet sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet esasları](../extensibility/internals/service-essentials.md)
