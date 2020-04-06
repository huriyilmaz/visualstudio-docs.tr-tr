---
title: VSPackages Yükleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702962"
---
# <a name="load-vspackages"></a>Yük VSPackages
VSPackages Visual Studio'ya yalnızca işlevsellikleri gerektiğinde yüklenir. Örneğin, Visual Studio bir proje fabrikasını veya VSPackage'ın uyguladığı bir hizmeti kullandığında bir VSPackage yüklenir. Bu özellik, performansı artırmak için mümkün olduğunda kullanılan gecikmeli yükleme olarak adlandırılır.

> [!NOTE]
> Visual Studio, VSPackage'ı yüklemeden, bir VSPackage'ın sunduğu komutlar gibi belirli VSPackage bilgilerini belirleyebilir.

 VSPackages belirli bir kullanıcı arabirimi (UI) bağlamında otomatik olarak ayarlanabilir, örneğin, bir çözüm açık olduğunda. Öznitelik <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> bu bağlamı ayarlar.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Bir VSPackage'ı belirli bir bağlamda otomatik yükleme

- VSPackage `ProvideAutoLoad` özniteliklerine öznitelik ekleyin:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     UI bağlamlarının ve <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> GUID değerlerinin listesi için numaralandırılmış alanlarına bakın.

- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Yöntemde bir kesme noktası ayarlayın.

- VSPackage'ı oluşturun ve hata ayıklamaya başlayın.

- Bir çözüm yükleyin veya bir çözüm oluşturun.

     VSPackage, kesme noktasında yükler ve durur.

## <a name="force-a-vspackage-to-load"></a>VsPackage'ı yüklemeye zorla
 Bazı durumlarda bir VSPackage başka bir VSPackage yüklenmesi için zorlamak zorunda kalabilir. Örneğin, hafif bir VSPackage, CMDUIContext olarak kullanılamayan bir bağlamda daha büyük bir VSPackage yükleyebilir.

 Bir VSPackage'ı yüklemeye zorlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> yöntemi kullanabilirsiniz.

- Bu kodu, başka <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> bir VSPackage'ı yüklemeye zorlayan VSPackage yöntemine ekleyin:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     VSPackage başharfe atıldığında, `PackageToBeLoaded` yüklemeye zorlanır.

     VSPackage iletişimi için kuvvet yüklemesi kullanılmamalıdır. Kullanımı kullanın ve bunun yerine [hizmetleri sağlayın.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
