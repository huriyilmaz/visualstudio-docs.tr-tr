---
title: Visual Studio 2022 önizlemesinde apı 'ler kaldırıldı
description: Visual Studio 2022 önizlemesinde kaldırılan VS SDK apı 'leri hakkında bilgi edinmek için uzantıları güncelleştirme Visual Studio 2022 önizleme ile çalışacak uzantı yazarları.
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
ms.openlocfilehash: cac7b6bcc3e6313e36c97b76a140a25e589d571b
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439788"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK tarafından kaldırılan apı 'ler

[!INCLUDE [preview-note](../includes/preview-note.md)]

aşağıdaki apı 'ler Visual Studio SDK 'dan kaldırılmıştır ve artık kullanılamaz, kodunuzu güncelleştirme hakkında ayrıntılı bilgi edinmek için lütfen her bölüme bakın.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` ' `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Zaman uyumsuz çözüm yükü ve basit çözüm yükü](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Kaynak güvenle aç](#open-from-source-safe)
* [.NET Framework için yeni WPF XAML Tasarımcısı](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>Isıfmageservice

`IVsImageService`Visual Studio 2022 ' de kaldırılıyor. Tüm kullanıcıları `IVsImageService` bunun yerine öğesine taşınmaya melidir `IVsImageService2` .

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Kullanırsanız `IVsImageService` , çağrıları üzerinde denk yöntemlere yapılan çağrılar ile yöntemleri ile değiştirin `IVsImageService2` :

| **Isımageservice yöntemi** | **Denk IVsImageService2 yöntemi** |
|----------------------------|----------------------------------------|
| Ekle                        | Addcustomımage                         |
| Al                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`öğesinin ekleme ve get yöntemleri, bilinen bir ad değil, özel görüntülere ada (bir dize) başvuruda bulunurlar.  Özel görüntülere başvurmak için kodunuzu yalnızca takma adlar kullanacak şekilde geçmeniz tercih edilir, ancak bu kanıtlar, `IVsImageService2` bir adı bilinen bir ad ile ilişkilendirmenize olanak tanıyan birkaç yöntem daha varsa:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Bu iki yöntemi kullanarak, görüntülere ada göre başvurulmasına devam edebilirsiniz.

## <a name="iblockcontextprovider"></a>Iblockcontextprovider

`IBlockContextProvider`ve ilgili türler Visual Studio 2022 ' de kaldırılıyor. Tüm kullanıcıları `IBlockContextProvider` bunun yerine öğesine taşınmaya melidir `IStructureContextSourceProvider` .

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Kullanıcıları `IBlockContextProvider` `IStructureContextSourceProvider` bunun yerine kullanması gerekir ([Belgeler](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>Itooltipprovider

`IToolTipProvider`ve ilgili türler Visual Studio 2022 ' de kaldırılıyor. Tüm kullanıcıları `IToolTipProvider` bunun yerine öğesine taşınmaya melidir `IToolTipService` .

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Kullanıcıları `IToolTipProvider` `IToolTipService` bunun yerine kullanması gerekir ([Belgeler](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>Ivstestextscanner ve ıvsfulltextscanner

`IVsTextScanner`ve `IVsFullTextScanner` Visual Studio 2022 ' de kaldırılıyor. Ya da ' ın tüm kullanıcıları `IVsTextScanner` `IVsFullTextScanner` bunun yerine öğesine taşınmaya melidir `IVsTextLines` .

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

`IVsTextScanner` `IVsFullTextScanner` Bunun yerine kullanıcıları veya kullanması gerekir `IVsTextLines` ([belgeleri](/dotnet/api/microsoft.visualstudio.textmanager.interop.ivstextlines.getlinetext).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Zaman uyumsuz çözüm yükü ve basit çözüm yükü

zaman uyumsuz çözüm yükü (asl) ve basit çözüm yükü (lsl) özellikleri Visual Studio 2022 ' de kaldırılıyor, çünkü aşağıdaki yöntemler kaldırılıyor:

### <a name="interfaces"></a>Arabirimler

* `IVsSolution4` -Yöntemler: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` -Yöntemler: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` -Tüm arabirim
* `IVsSolutionLoadManager` -Tüm arabirim
* `IVsSccManager3`  -Tüm arabirim
* `IVsAsynchronousProjectCreate` -Tüm arabirim
* `IVsAsynchronousProjectCreateUI` -Tüm arabirim

### <a name="enums-properties-and-ui-contexts"></a>Numaralandırmalar, Özellikler ve UI bağlamları

* `VSHPROPID_ProjectUnloadStatus` Yardımının `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok.

## <a name="ivsdummy"></a>Isdummy

`IVsDummy`Visual Studio 2022 ' de kaldırılıyor ve değiştirilmeyecektir. 

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok. Ancak, API hiçbir şey olmadığı için bir etkisi olmamalıdır.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft. VisualStudio. Shell. Task

`Microsoft.VisualStudio.Shell.Task`Sınıfı, `Microsoft.VisualStudio.Shell.TaskListItem` çok popüler sınıfla çakışmayacak şekilde olarak yeniden adlandırıldı `System.Threading.Tasks.Task` .

## <a name="open-from-source-safe"></a>Kaynak güvenle aç

Aşağıdaki yöntemler, olaylar ve, sabitler kaldırıldıkça, kaynak güvenle bir çözüm açmaya yönelik destek kaldırılıyor.

## <a name="interfaces"></a>Arabirimler

* `IVsSCCProvider3` -Tüm arabirim

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Yok.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>.NET Framework için yeni WPF XAML Tasarımcısı

.NET Framework için geçerli wpf XAML Tasarımcısı kullanımdan kaldırılmıştır ve .net için wpf XAML Tasarımcısı (.net Core) için kullanılan mimariye göre .NET Framework için yeni bir WPF XAML Tasarımcısı ile değiştirilmelidir. bu ayrıca WPF .NET Framework. design.dll ve Microsoft tabanlı genişletilebilirlik modelini kontrol etmek anlamına gelir. Windows. Design. Extensibility artık desteklenmiyor. .NET Framework için yeni wpf XAML Tasarımcısı, .net için wpf XAML Tasarımcısı aynı genişletilebilirlik modelini sağlayacaktır (.net Core). .NET (.NET Core) için bir. designtools.dll uzantısı zaten oluşturduysanız, aynı uzantı .NET Framework yeni WPF XAML Tasarımcısı için de çalışacaktır. WPF platformları için yeni genişletilebilirlik modeline (.NET Framework ve .net Core) ve daha ileri hareket eden UWP platformlarına geçiş yapma hakkında daha fazla bilgi için lütfen aşağıdaki geçiş bağlantısına bakın. 

### <a name="recommended-updates"></a>Önerilen güncelleştirmeler

Bkz. [XAML Tasarımcısı genişletilebilirlik geçişi](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md).
