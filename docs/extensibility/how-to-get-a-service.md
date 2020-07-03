---
title: 'Nasıl yapılır: hizmet alma | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a401103112096a1089b59ba3733d19480f93e891
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905827"
---
# <a name="how-to-get-a-service"></a>Nasıl yapılır: hizmet alma

Farklı özelliklere erişmek için genellikle Visual Studio Hizmetleri 'ni almanız gerekir. Genel olarak, bir Visual Studio hizmeti kullanabileceğiniz bir veya daha fazla arabirim sağlar. Bir VSPackage 'tan birçok hizmeti alabilirsiniz.

' Den türetilen ve doğru şekilde oluşturulmuş herhangi bir VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> herhangi bir genel hizmeti isteyebilir. `Package`Sınıfı uyguladığı için <xref:System.IServiceProvider> , öğesinden türetilen herhangi bir VSPackage `Package` da bir hizmet sağlayıcıdır.

Visual Studio bir yüklediğinde <xref:Microsoft.VisualStudio.Shell.Package> , <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> başlatma sırasında yöntemine bir nesnesi geçirir. Bu, VSPackage 'ın *ele alınmasına* denir. `Package`Sınıfı bu hizmet sağlayıcısını sarmalayan ve hizmet <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> alma yöntemi sağlar.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Başlatılmış bir VSPackage hizmetinden hizmet alma

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projesi oluşturun `GetServiceExtension` . "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Şimdi **GetServiceCommand**adlı özel bir komut öğesi şablonu ekleyin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *GetServiceCommand.cs*olarak değiştirin. Özel bir komut oluşturma hakkında daha fazla bilgi için, [bir menü komutuyla bir uzantı oluşturun](../extensibility/creating-an-extension-with-a-menu-command.md)

3. *GetServiceCommand.cs*içinde, yönteminin gövdesini kaldırın `MenuItemCommand` ve aşağıdaki kodu ekleyin:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Bu kod, bir SVsActivityLog hizmeti alır ve bunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılabilecek bir arabirime yayınlar. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

5. Deneysel örneğin **Araçlar** menüsünde **Getservicekomutunu çağır** düğmesini bulun. Bu düğmeye tıkladığınızda, **etkinlik günlüğü hizmetini bulunan** bir ileti kutusu görmeniz gerekir.

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Bir araç penceresi veya denetim kapsayıcısından hizmet alma

Bazen bir araç penceresi veya denetim kapsayıcısından bir hizmet almanız ya da başka bir hizmet sağlayıcı ile istediğiniz hizmet hakkında bilgi sahibi olmaması gerekebilir. Örneğin, bir denetim içinden etkinlik günlüğüne yazmak isteyebilirsiniz.

Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Yöntem, ' den türetilen herhangi bir VSPackage ilk kez başlatılan önbelleğe alınmış bir hizmet sağlayıcısına bağımlıdır <xref:Microsoft.VisualStudio.Shell.Package> .

VSPackage devre dışı bırakmadan VSPackage Oluşturucusu çağrıldığından, genel hizmetler genellikle VSPackage oluşturucusunun içinden kullanılamaz. Bkz. [nasıl yapılır: geçici çözüm hizmetleri sorunlarını giderme](../extensibility/how-to-troubleshoot-services.md) .

Bir araç penceresinde veya diğer VSPackage öğesi olmayan bir hizmeti almak için bir yol örneği aşağıda verilmiştir.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE nesnesinden bir hizmet alma

Ayrıca, nesnesinden hizmetleri de alabilirsiniz <xref:EnvDTE.DTEClass> . Ancak, DTE nesnesini VSPackage 'dan bir hizmet olarak veya static yöntemi çağırarak almalısınız <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

DTE nesnesi <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , kullanarak bir hizmeti sorgulamak için kullanabileceğiniz öğesini uygular <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

DTE nesnesinden bir hizmeti alma hakkında daha fazla bilgiyi burada bulabilirsiniz.

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

- [Nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [Service Essentials](../extensibility/internals/service-essentials.md)
