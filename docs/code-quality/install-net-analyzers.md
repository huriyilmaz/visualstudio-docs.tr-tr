---
title: Birinci taraf .NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi
ms.date: 08/03/2018
description: .NET SDK 'dan birinci taraf .NET Çözümleyicileri 'ni etkinleştirmeyi veya bu Çözümleyicileri bir NuGet paketi olarak yüklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ea13fde64f6214cf3c219de45c79458b75e1caf8
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615531"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Birinci taraf .NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi

## <a name="overview"></a>Genel Bakış

.NET derleyici platformu (Roslyn) çözümleyicileri, C# veya Visual Basic kodunuzda kod kalitesi ve kod stili sorunları olup olmadığını inceler. Birinci taraf .NET Çözümleyicileri, **hedef platform belirsiz**' dir. Diğer bir deyişle, projenizin belirli bir .NET platformunu hedeflemesi gerekmez. Çözümleyiciler, `net5.0` ve gibi önceki .NET sürümlerinin yanı sıra hedeflenen projeler için de çalışır `netcoreapp` `netstandard` `net472` .

Birinci taraf .NET Çözümleyicileri 'ni aşağıdaki yollarla etkinleştirebilir veya yükleyebilirsiniz:

- **.NET SDK 'Dan etkinleştir**: Visual Studio 2019 16,8 ve .NET 5,0 'den başlayarak, bu çözümleyiciler [.NET SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). Varsayılan olarak, .NET 5,0 veya üstünü hedefleyen projeler için analiz etkindir. Özelliğini olarak ayarlayarak, önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` . Ayrıca, olarak ayarlayarak projeniz için kod analizini devre dışı bırakabilirsiniz `EnableNETAnalyzers` `false` .

- **NuGet paketi olarak yükleyebilirsiniz**: .NET 5 + SDK ' ya geçmek istemiyorsanız veya bir NuGet paket tabanlı modeli tercih ediyorsanız, çözümleyiciler `Microsoft.CodeAnalysis.NetAnalyzers` Visual Studio 2019 üzerinde [NuGet paketinde](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) de mevcuttur.  İsteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edebilirsiniz. Visual Studio 2017 kullanıyorsanız, `2.9.x` `Microsoft.CodeAnalysis.FxCopAnalyzers` bunun yerine [NuGet paketinin](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) en son sürümünü yükleyebilirsiniz.

> [!NOTE]
> `Microsoft.CodeAnalysis.NetAnalyzers`Mümkün olduğunda, [NuGet paketini](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)yüklemek yerine, çözümleyiciler .NET SDK 'dan etkinleştirmeniz önerilir. .NET SDK 'dan Çözümleyicileri etkinleştirmek, SDK 'Yı güncelleştirdikten hemen sonra otomatik olarak çözümleyici hata düzeltmeleri ve yeni çözümleyiciler almanızı sağlar. NuGet modelinde, en son hata düzeltmelerini istediğiniz her seferinde NuGet paketini güncelleştirmeniz gerekir. NuGet paketi daha sık güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod Çözümleyicileri 'ne genel bakış](roslyn-analyzers-overview.md)
- [Visual Studio 'da kod Çözümleyicileri kullanma](use-roslyn-analyzers.md)
- [Eski analizden .NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
