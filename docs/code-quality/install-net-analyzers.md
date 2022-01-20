---
title: Birinci taraf .NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi
ms.date: 01/13/2022
description: .net SDK 'dan birinci taraf .net çözümleyicileri 'ni etkinleştirmeyi veya bu çözümleyicileri NuGet bir paket olarak yüklemeyi öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 15d4322fdd50f3d6c71bf00ef6f5c1a7bbaefceb
ms.sourcegitcommit: 2a8c7de72f952203289459736107c875837bb07e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137110094"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Birinci taraf .NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi

## <a name="overview"></a>Genel Bakış

.NET derleyici platformu (Roslyn) çözümleyicileri, C# veya Visual Basic kodunuzda kod kalitesi ve kod stili sorunları olup olmadığını inceler. Birinci taraf .NET Çözümleyicileri, **hedef platform belirsiz**' dir. Diğer bir deyişle, projenizin belirli bir .NET platformunu hedeflemesini gerektirmez. Çözümleyiciler, ve gibi önceki .NET sürümlerini hedefleyen projeler için çalışır `net5.0` `netcoreapp` `netstandard` `net472` .

Birinci taraf .NET Çözümleyicileri 'ni aşağıdaki yollarla etkinleştirebilir veya yükleyebilirsiniz:

- **.net sdk 'dan etkinleştir**: 2019 16,8 ve .net 5,0 Visual Studio başlayarak, bu çözümleyiciler [.net sdk 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). Varsayılan olarak, .NET 5,0 veya üstünü hedefleyen projeler için analiz etkindir. MSBUILD [Enablenetçözümleyiciler](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) özelliğini olarak ayarlayarak, daha önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz `true` . Ayrıca, olarak ayarlayarak projeniz için kod analizini devre dışı bırakabilirsiniz `EnableNETAnalyzers` `false` .

- **NuGet paketi olarak yükleyebilirsiniz**: .net 5 + SDK ' ya geçmek istemiyorsanız veya bir NuGet paket tabanlı model tercih ediyorsanız, çözümleyiciler `Microsoft.CodeAnalysis.NetAnalyzers` Visual Studio 2019 ' deki [NuGet paketinde](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) de mevcuttur.  İsteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edebilirsiniz. Visual Studio 2017 kullanıyorsanız, `2.9.x` `Microsoft.CodeAnalysis.FxCopAnalyzers` bunun yerine [NuGet paketinin](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) en son sürümünü yükleyebilirsiniz.

> [!NOTE]
> `Microsoft.CodeAnalysis.NetAnalyzers`mümkün olduğunda, [NuGet paketini](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)yüklemek yerine, çözümleyiciler .net SDK 'dan etkinleştirmeniz önerilir. .NET SDK 'dan Çözümleyicileri etkinleştirmek, SDK 'Yı güncelleştirdikten hemen sonra otomatik olarak çözümleyici hata düzeltmeleri ve yeni çözümleyiciler almanızı sağlar. NuGet modelinde, en son hata düzeltmelerini istediğiniz her seferinde NuGet paketi güncelleştirmeniz gerekir. NuGet paketi daha sık güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'de kod Çözümleyicileri 'ne genel bakış](roslyn-analyzers-overview.md)
- [Visual Studio 'de kod Çözümleyicileri kullanma](use-roslyn-analyzers.md)
- [Eski analizden .NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
