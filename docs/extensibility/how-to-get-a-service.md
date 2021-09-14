---
title: 'Nasıl |: Hizmet | Microsoft Docs'
description: Farklı özelliklere erişmek Visual Studio hizmetleri nasıl elde etmeyi öğrenin. Çoğu hizmeti VSPackage kullanarak eldeabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 810211f79bd04bcba9b59dcf60e16e14d19bc702
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626253"
---
# <a name="how-to-get-a-service"></a>Nasıl: Hizmet al

Farklı özelliklere erişmek için genellikle Visual Studio hizmetlere erişmeye ihtiyacınız olur. Genel olarak, Visual Studio hizmeti kullanabileceğiniz bir veya daha fazla arabirim sağlar. Çoğu hizmeti VSPackage'dan eldeabilirsiniz.

ve'den türetilmiş ve doğru şekilde siteli herhangi bir VSPackage <xref:Microsoft.VisualStudio.Shell.Package> herhangi bir genel hizmet sorabilir. sınıfı `Package` uygulaması <xref:System.IServiceProvider> nedeniyle, 'den türeten herhangi bir VSPackage `Package` aynı zamanda bir hizmet sağlayıcısıdır.

Bir Visual Studio <xref:Microsoft.VisualStudio.Shell.Package> yüklerken, başlatma sırasında <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> yöntemine bir nesnesi iletir. Buna *VSPackage'da siting* denir. sınıfı `Package` bu hizmet sağlayıcısını sarmalar ve hizmetleri <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> almak için yöntemini sağlar.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Başlatılan VSPackage'dan hizmet alma

1. Her Visual Studio uzantı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. adlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi `GetServiceExtension` oluşturun. VSIX proje şablonunu New **Project** "vsix" arayarak bulabilirsiniz.

2. Şimdi **GetServiceCommand** adlı özel bir komut öğesi şablonu ekleyin. Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Özel **Komut'ı seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *GetServiceCommand.cs olarak değiştirebilirsiniz.* Özel komut oluşturma hakkında daha fazla bilgi için Menü [komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

3. *GetServiceCommand.cs* içinde yönteminin `MenuItemCommand` gövdeyi kaldırın ve aşağıdaki kodu ekleyin:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Bu kod bir SVsActivityLog hizmetini alır ve bunu etkinlik günlüğüne yazmak için kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> bir arabirime yazar. Bir örnek için, [bkz. Nasıl: Etkinlik günlüğünü kullanma.](../extensibility/how-to-use-the-activity-log.md)

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

5. Deneysel **örneğin** Araçlar menüsünde **GetServiceCommand çağır düğmesini** bulun. Bu düğmeye tıklarsanız etkinlik günlüğü hizmetinin bulundu olduğunu **söyleyen bir ileti kutusu görüyorsanız.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Araç penceresinden veya denetim kapsayıcılarından hizmet alma

Bazen, bir araç penceresinden veya sited 2019'da yer almayan veya istediğiniz hizmeti bilmiyor bir hizmet sağlayıcısıyla siteli olan kapsayıcıyı denetlemeniz gerekebilir. Örneğin, bir denetimden etkinlik günlüğüne yazmak istiyor olabilir.

Statik yöntem, türetilen herhangi bir VSPackage ilk kez sited ilk kez başlatılan <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> önbelleğe alınmış bir <xref:Microsoft.VisualStudio.Shell.Package> hizmet sağlayıcısını kullanır.

VSPackage oluşturucusu VSPackage sited olmadan önce çağrıldıklarından, genel hizmetler genellikle VSPackage oluşturucusu içinde kullanılamaz. Geçici [bir çözüm için bkz. Nasıl yapılanlar:](../extensibility/how-to-troubleshoot-services.md) Hizmetlerle ilgili sorunları giderme.

Burada bir araç penceresinde veya VSPackage olmayan başka bir öğede hizmet elde etmek için bir örnek veserge ve sonra bir örnek veserge ve sonra da bir hizmet edinebilirsiniz.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE nesnesinden hizmet alma

Hizmetleri nesnesinden de elde <xref:EnvDTE.DTEClass> edersiniz. Ancak, vsPackage'dan hizmet olarak veya statik yöntemi çağırarak DTE nesnesini <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> alalız.

DTE nesnesi, kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> bir hizmeti sorgulamak için kullanabileceğiniz nesnesini <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> kullanır.

DTE nesnesinden hizmet almak için aşağıdakiler kullanılır.

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

- [Nasıl: Hizmet sağlama](../extensibility/how-to-provide-a-service.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet temelleri](../extensibility/internals/service-essentials.md)
