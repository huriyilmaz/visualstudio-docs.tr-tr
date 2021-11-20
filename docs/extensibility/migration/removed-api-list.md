---
title: Visual Studio 2022'de API'ler kaldırıldı
description: Visual Studio 2022'de kaldırılan VS SDK API'leri hakkında bilgi edinmek ve uzantı yazarlarının uzantılarını 2022'de Visual Studio öğrenin.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: d2edf8cbfca8d4ae26c3b6a67a49c389b2f46379
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132879719"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK API'leri kaldırıldı

Aşağıdaki API'ler Visual Studio SDK'dan kaldırılmıştır ve artık kullanılamaz. Kodunuzu güncelleştirme hakkında ayrıntılı bilgi için lütfen her bölüme bakın.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` Ve `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Zaman uyumsuz çözüm yükü ve basit çözüm yükü](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Kaynak kasadan açma](#open-from-source-safe)
* [Yeni XAML Tasarımcısı WPF .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

`IVsImageService`2022'de Visual Studio kaldırılıyor. Bunun yerine tüm `IVsImageService` kullanıcıları 'a `IVsImageService2` taşınarak.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

`IVsImageService`kullanırsanız, metotlarına yapılan çağrıları üzerinde eşdeğer yöntemlere yapılan çağrılarla `IVsImageService2` değiştirin:

| **IVsImageService Yöntemi** | **Eşdeğer IVsImageService2 Yöntemi** |
|----------------------------|----------------------------------------|
| Ekle                        | AddCustomImage                         |
| Al                        | Getımage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`'nin Ad yerine ad (dize) ile özel görüntülere başvurulan Add ve Get yöntemleri.  Kodunuzu özel görüntülere başvurmak için yalnızca bilinen adlar kullanmak üzere değiştirmeniz tercih edilir, ancak bunun pratik olmadığını kanıtlarsa, bir adı bilinen adla ilişkilendirmenize olanak sağlayacak birkaç yöntem `IVsImageService2` vardır:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Bu iki yöntemi kullanarak görüntülere adla başvuru yapmaya devam edersiniz.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

`IBlockContextProvider`2022'de ve Visual Studio kaldırılıyor. Bunun yerine tüm `IBlockContextProvider` kullanıcıları 'a `IStructureContextSourceProvider` taşınarak.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

kullanıcılarının `IBlockContextProvider` bunun yerine `IStructureContextSourceProvider` kullanmaları gerekir ([belgeler).](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)

## <a name="itooltipprovider"></a>IToolTipProvider

`IToolTipProvider`2022'de ve Visual Studio kaldırılıyor. Bunun yerine tüm `IToolTipProvider` kullanıcıları 'a `IToolTipService` taşınarak.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

kullanıcılarının `IToolTipProvider` bunun yerine `IToolTipService` kullanmaları gerekir ([belgeler).](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner ve IVsFullTextScanner

`IVsTextScanner` `IVsFullTextScanner` 2022'de ve Visual Studio kaldırılıyor. Tüm veya kullanıcıları `IVsTextScanner` `IVsFullTextScanner` bunun yerine 'a taşın `IVsTextLines` uygulamalı.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

veya kullanıcıları `IVsTextScanner` bunun `IVsFullTextScanner` yerine `IVsTextLines` kullanmalı ([belgeleri).](/dotnet/api/microsoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Zaman uyumsuz çözüm yükü ve basit çözüm yükü

Zaman uyumsuz çözüm yükü (ASL) ve basit çözüm yükü (LSL) özellikleri Visual Studio 2022'de kaldırılıyor, bu nedenle aşağıdaki yöntemler kaldırılıyor:

### <a name="interfaces"></a>Arabirimler

* `IVsSolution4` - Yöntemler: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` - Yöntemler: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` - Tüm arabirim
* `IVsSolutionLoadManager` - Tüm arabirim
* `IVsSccManager3`  - Tüm arabirim
* `IVsAsynchronousProjectCreate` - Tüm arabirim
* `IVsAsynchronousProjectCreateUI` - Tüm arabirim

### <a name="enums-properties-and-ui-contexts"></a>Enum'lar, özellikler ve UI bağlamları

* `VSHPROPID_ProjectUnloadStatus` - Enum: `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok.

## <a name="ivsdummy"></a>IVsDummy

`IVsDummy`, 2022'Visual Studio kaldırılıyor ve değiştirilemez. 

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok. Ancak API hiçbir şey yapmadı.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft.VisualStudio.Shell.Task

sınıfı, `Microsoft.VisualStudio.Shell.Task` çok popüler `Microsoft.VisualStudio.Shell.TaskListItem` sınıfla çakışmamaları için olarak yeniden `System.Threading.Tasks.Task` adlandırıldı.

## <a name="open-from-source-safe"></a>Kaynak kasadan açma

Aşağıdaki yöntemler, olaylar ve sabitler kaldırıldığı için kaynak kasadan çözüm açma desteği kaldırılıyor.

## <a name="interfaces"></a>Arabirimler

* `IVsSCCProvider3` - Tüm arabirim

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Yeni XAML Tasarımcısı WPF .NET Framework

.NET Framework için geçerli WPF XAML Tasarımcısı kullanım dışı bırakıldı ve .NET (.NET Core) için WPF XAML Tasarımcısı için kullanılan mimariye göre .NET Framework için yeni bir WPF XAML Tasarımcısı ile değiştirilir. Bu, WPF'nin ..NET Framework ve Microsoft.design.dll tabanlı genişletilebilirlik modelini Windows. Design.Genişletilebilirlik artık desteklenmiyor. .NET Framework için yeni WPF XAML Tasarımcısı, .NET (.NET Core) için WPF XAML Tasarımcısı aynı genişletilebilirlik modelini sağlayacaktır. .NET (.NET Coredesigntools.dll için zaten bir .designtools.dll uzantısı oluşturduysanız, bu uzantı yeni WPF XAML Tasarımcısı için .NET Framework. WPF platformları (.NET Framework ve .NET Core) ve UWP platformları için yeni genişletilebilirlik modeline geçiş hakkında daha fazla bilgi için lütfen aşağıdaki geçiş bağlantısına bakın. 

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Bkz. [XAML tasarımcısı genişletilebilirlik geçişi.](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)
