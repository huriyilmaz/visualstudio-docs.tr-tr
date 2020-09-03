---
title: VSPackages yükleniyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702962"
---
# <a name="load-vspackages"></a>VSPackages yükleme
VSPackages, yalnızca işlevleri gerekli olduğunda Visual Studio 'ya yüklenir. Örneğin, Visual Studio bir proje fabrikası veya VSPackage 'ın uyguladığı bir hizmet kullandığında VSPackage yüklenir. Bu özellik Gecikmeli yükleme olarak adlandırılır ve performansı artırmak için kullanılır.

> [!NOTE]
> Visual Studio, VSPackage 'ı yüklemeden VSPackage tarafından sunulan komutlar gibi belirli VSPackage bilgilerini belirleyebilir.

 VSPackages, belirli bir kullanıcı arabirimi (UI) bağlamında, örneğin bir çözüm açık olduğunda, tekrar yükleme olarak ayarlanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Özniteliği bu bağlamı ayarlar.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Belirli bir bağlamda VSPackage 'ı oto yükleme

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

## <a name="force-a-vspackage-to-load"></a>VSPackage yüklemesine zorla
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

     Zorla yükleme, VSPackage iletişimi için kullanılmamalıdır. [Kullanın ve bunun yerine hizmetleri sağlayın](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
