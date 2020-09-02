---
title: 'Nasıl yapılır: hizmet alma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ef86b8cde506aad3e00aa6b5dbc6470c0087de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204181"
---
# <a name="how-to-get-a-service"></a>Nasıl Yapılır: Hizmet Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı özelliklere erişmek için genellikle Visual Studio Hizmetleri 'ni almanız gerekir. Genel olarak, bir Visual Studio hizmeti kullanabileceğiniz bir veya daha fazla arabirim sağlar. Bir VSPackage 'tan birçok hizmeti alabilirsiniz.  
  
 ' Den türetilen ve doğru şekilde oluşturulmuş herhangi bir VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> herhangi bir genel hizmeti isteyebilir. Paket sınıfı uyguladığı için <xref:System.IServiceProvider> , paketten türetilen herhangi bir VSPackage aynı zamanda bir hizmet sağlayıcıdır.  
  
 Visual Studio bir yüklediğinde <xref:Microsoft.VisualStudio.Shell.Package> , <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> başlatma sırasında yöntemine bir nesnesi geçirir. Bu, VSPackage 'ın *ele alınmasına* denir. Paket sınıfı bu hizmet sağlayıcısını sarmalayan ve hizmet <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> alma yöntemi sağlar.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Başlatılmış bir VSPackage hizmetinden hizmet alma  
  
1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX projesi oluşturun `GetServiceExtension` . VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Şimdi **GetServiceCommand**adlı özel bir komut öğesi şablonu ekleyin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **GetServiceCommand.cs**olarak değiştirin. Özel bir komut oluşturma ve [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md) hakkında daha fazla bilgi için  
  
3. GetServiceCommand.cs ' de, Menuıtemcommand yönteminin gövdesini kaldırın ve aşağıdaki kodu ekleyin:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Bu kod, bir SVsActivityLog hizmeti alır ve bunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılabilecek bir arabirime yayınlar. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).  
  
4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.  
  
5. Deneysel örneğin Araçlar menüsünde **Getservicekomutunu çağır** düğmesini bulun. Bu düğmeye tıkladığınızda, **etkinlik günlüğü hizmetini bulunan** bir ileti kutusu görmeniz gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)
