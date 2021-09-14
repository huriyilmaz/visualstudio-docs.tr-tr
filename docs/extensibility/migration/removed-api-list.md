---
title: Visual Studio 2022 Preview'da API'ler kaldırıldı
description: Visual Studio 2022 Preview'da kaldırılan VS SDK API'leri hakkında bilgi edinin. Uzantı yazarlarının uzantılarını Visual Studio 2022 Preview sürümüyle çalışacak şekilde güncelleştirmeleri.
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
ms.openlocfilehash: 4501fdb465452eff1623e39c50e8c97f3bb5ca5b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726903"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK API'leri kaldırıldı

[!INCLUDE [preview-note](../includes/preview-note.md)]

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

`IVsImageService`'nin Ad yerine ad (dize) ile özel görüntülere başvurulan Add ve Get yöntemleri.  Kodunuzu özel görüntülere başvurmak için yalnızca bilinen adlar kullanmak üzere değiştirmeniz tercih edilir, ancak bu pratik olmadığını kanıtlarsa, bir adı bilinen adla ilişkilendirmenize olanak sağlayacak birkaç yöntem `IVsImageService2` vardır:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Bu iki yöntemi kullanarak görüntülere adla başvuru yapmaya devam edersiniz.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

`IBlockContextProvider`2022'de ve Visual Studio kaldırılıyor. Bunun yerine tüm `IBlockContextProvider` kullanıcıları 'a `IStructureContextSourceProvider` taşınarak.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

kullanıcıları bunun `IBlockContextProvider` yerine `IStructureContextSourceProvider` (belgeler)[kullandır.](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)

## <a name="itooltipprovider"></a>IToolTipProvider

`IToolTipProvider`2022'de ve Visual Studio kaldırılıyor. Bunun yerine tüm `IToolTipProvider` kullanıcıları 'a `IToolTipService` taşınarak.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

kullanıcıları bunun `IToolTipProvider` yerine `IToolTipService` (belgeler)[kullandır.](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner ve IVsFullTextScanner

`IVsTextScanner` `IVsFullTextScanner` 2022'de ve Visual Studio kaldırılıyor. Tüm veya kullanıcıları `IVsTextScanner` `IVsFullTextScanner` bunun yerine 'a taşın `IVsTextLines` uygulamalı.

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

veya kullanıcıları `IVsTextScanner` bunun `IVsFullTextScanner` yerine `IVsTextLines` kullanmaları gerekir ([belgeler).](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)

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

.NET Framework için geçerli WPF XAML Tasarımcısı kullanım dışı bırakıldı ve .NET (.NET Core) için WPF XAML Tasarımcısı için kullanılan mimariye göre .NET Framework için yeni bir WPF XAML Tasarımcısı ile değiştirilir. Bu, WPF'nin ..NET Framework ve Microsoft'u temel alan genişletilebilirlik modelini design.dll anlamına gelir. Windows. Design.Genişletilebilirlik artık desteklenmiyor. .NET Framework için yeni WPF XAML Tasarımcısı, .NET (.NET Core) için WPF XAML Tasarımcısı aynı genişletilebilirlik modelini sağlayacaktır. .NET (.NET Coredesigntools.dll için zaten bir .designtools.dll uzantısı oluşturduysanız, bu uzantı yeni WPF XAML Tasarımcısı için .NET Framework. WPF platformları (.NET Framework ve .NET Core) ve UWP platformları için yeni genişletilebilirlik modeline geçiş hakkında daha fazla bilgi için lütfen aşağıdaki geçiş bağlantısına bakın. 

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Bkz. [XAML tasarımcısı genişletilebilirlik geçişi.](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)
