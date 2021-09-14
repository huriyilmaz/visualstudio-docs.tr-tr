---
title: VSPackage'ları | Microsoft Docs
description: Performansı geliştirmek için mümkün olduğunda kullanılan gecikmeli yükleme Visual Studio vsPackage'ları yükleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d56192fed9138e6edd8f18753893b195c174c5b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628893"
---
# <a name="load-vspackages"></a>VSPackage'ları yükleme
VSPackage'lar Visual Studio işlevleri gerektiğinde yüklenir. Örneğin, proje fabrikası veya VSPackage'Visual Studio bir hizmet kullanan bir VSPackage yüklenir. Bu özellik gecikmeli yükleme olarak adlandırılan ve performansı geliştirmek için mümkün olan her durumda kullanılır.

> [!NOTE]
> Visual Studio VSPackage'ın sunduğu komutlar gibi belirli VSPackage bilgilerini VSPackage yüklemeden belirleyebilirsiniz.

 VSPackage'lar belirli bir kullanıcı arabirimi (UI) bağlamında (örneğin, bir çözüm açık olduğunda) otomatik olarak yük devredebilir. özniteliği <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> bu bağlamı ayarlar.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>VSPackage'i belirli bir bağlamda otomatik olarak yükleme

- `ProvideAutoLoad`VSPackage özniteliklerine özniteliğini ekleyin:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Kullanıcı arabirimi bağlamlarının ve GUID değerlerinin listesi için numaralanmış <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> alanlarına bakın.

- yönteminde bir kesme noktası <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ayarlayın.

- VSPackage'ı derleme ve hata ayıklamayı başlatma.

- Bir çözüm yükleme veya oluşturma.

     VSPackage yüklenir ve kesme noktası içinde durur.

## <a name="force-a-vspackage-to-load"></a>VSPackage'i yüklenmeye zorlama
 Bazı durumlarda vsPackage'ın başka bir VSPackage'ın yüklenmeye zor olması gerekir. Örneğin, basit bir VSPackage, CMDUIContext olarak mevcut olmayan bir bağlamda daha büyük bir VSPackage'i yükleyemedi.

 Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> VSPackage'ın yüklenmeye zorln için yöntemini kullanabilirsiniz.

- Bu kodu başka bir <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackage'ın yüklenmeye neden olduğu VSPackage yöntemine girin:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     VSPackage başlatıldıktan sonra yüklenmeye `PackageToBeLoaded` zorlar.

     VSPackage iletişimi için zorla yükleme kullanılmamalı. Bunun [yerine Kullanın ve hizmet sağlamayı](../extensibility/using-and-providing-services.md) kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
