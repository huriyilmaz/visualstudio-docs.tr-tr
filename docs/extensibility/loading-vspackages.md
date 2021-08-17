---
title: VSPackages yükleniyor | Microsoft Docs
description: performansı artırmak için mümkün olduğunda kullanılan gecikmeli yükleme de dahil olmak üzere Visual Studio vspackages yükleme hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041730"
---
# <a name="load-vspackages"></a>VSPackages yükleme
vspackages, yalnızca işlevleri gerekli olduğunda Visual Studio yüklenir. örneğin, Visual Studio bir proje fabrikası veya vspackage 'ın uyguladığı bir hizmeti kullandığında vspackage yüklenir. Bu özellik Gecikmeli yükleme olarak adlandırılır ve performansı artırmak için kullanılır.

> [!NOTE]
> Visual Studio, vspackage 'ı yüklemeden, vspackage tarafından sunulan komutlar gibi belirli vspackage bilgilerini belirleyebilir.

 VSPackages, belirli bir kullanıcı arabirimi (UI) bağlamında, örneğin bir çözüm açık olduğunda, tekrar yükleme olarak ayarlanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Özniteliği bu bağlamı ayarlar.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Belirli bir bağlamda VSPackage 'ı oto yükleme

- `ProvideAutoLoad`Özniteliğini VSPackage özniteliklerine ekleyin:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
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
