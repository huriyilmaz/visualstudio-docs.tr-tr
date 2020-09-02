---
title: VSPackages yükleniyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802267"
---
# <a name="loading-vspackages"></a>VSPackage Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages, yalnızca işlevleri gerekli olduğunda Visual Studio 'ya yüklenir. Örneğin, Visual Studio bir proje fabrikası veya VSPackage 'ın uyguladığı bir hizmet kullandığında VSPackage yüklenir. Bu özellik Gecikmeli yükleme olarak adlandırılır ve performansı artırmak için kullanılır.  
  
> [!NOTE]
> Visual Studio, VSPackage 'ı yüklemeden VSPackage tarafından sunulan komutlar gibi belirli VSPackage bilgilerini belirleyebilir.  
  
 VSPackages, belirli bir kullanıcı arabirimi (UI) bağlamında, örneğin bir çözüm açık olduğunda, tekrar yükleme olarak ayarlanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Özniteliği bu bağlamı ayarlar.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Belirli bir bağlamda VSPackage 'ı oto yükleme  
  
- `ProvideAutoLoad`Özniteliğini VSPackage özniteliklerine ekleyin:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Kullanıcı arabirimi bağlamlarının listesi ve BUNLARıN GUID değerleri için bkz. öğesinin numaralandırılmış alanları.  
  
- Yönteminde bir kesme noktası ayarlayın <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
- VSPackage oluşturun ve hata ayıklamayı başlatın.  
  
- Bir çözüm yükleyin veya oluşturun.  
  
     VSPackage, kesme noktasında yüklenir ve duraklar.  
  
## <a name="forcing-a-vspackage-to-load"></a>VSPackage yüklenmeye zorlanıyor  
 Bazı koşullarda, bir VSPackage 'ın başka bir VSPackage 'ın yüklenmesine zorlamak gerekebilir. Örneğin, hafif VSPackage, CMDUIContext olarak kullanılamayan bir bağlamda daha büyük bir VSPackage yükleyebilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>Bir VSPackage yüklemesine zorlamak için yöntemini kullanabilirsiniz.  
  
- Bu kodu <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> , başka bir VSPackage yüklemesine zorlayan VSPackage yöntemine ekleyin:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     VSPackage başlatıldığında `PackageToBeLoaded` yüklenmeye zorlanır.  
  
     Zorla yükleme, VSPackage iletişimi için kullanılmamalıdır. Bunun yerine [, kullanma ve hizmet sağlama](../extensibility/using-and-providing-services.md) kullanın.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>VSPackage kaydetmek için özel bir öznitelik kullanma  
 Belirli durumlarda, uzantınızın yeni bir kayıt özniteliğini oluşturmanız gerekebilir. Kayıt özniteliklerini kullanarak yeni kayıt defteri anahtarları ekleyebilir veya varolan anahtarlara yeni değerler ekleyebilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ve ve yöntemlerinin geçersiz kılması gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-registry-key"></a>Kayıt defteri anahtarı oluşturma  
 Aşağıdaki kodda, özel öznitelik, kayıtlı olan VSPackage için anahtar altında **özel** bir alt anahtar oluşturur.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluşturma  
 Varolan bir anahtara özel değerler ekleyebilirsiniz. Aşağıdaki kod, VSPackage kayıt anahtarına nasıl yeni bir değer ekleneceğini gösterir.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)
