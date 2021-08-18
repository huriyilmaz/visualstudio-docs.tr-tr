---
title: Birinci taraf .NET çözümleyicilerini etkinleştirme veya yükleme
ms.date: 08/03/2018
description: .NET SDK'dan birinci taraf .NET çözümleyicilerini etkinleştirmeyi veya bu çözümleyicileri bir uygulama paketi olarak NuGet öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 25d98bfd0ddbc691c6fbc1ce22a129f9c6cfa692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091285"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Birinci taraf .NET çözümleyicilerini etkinleştirme veya yükleme

## <a name="overview"></a>Genel Bakış

.NET derleyici platformu (Roslyn) çözümleyicileri, C# veya Visual Basic kodunuzda kod kalitesi ve kod stili sorunları olup olmadığını inceler. Birinci taraf .NET çözümleyicileri **hedef platformdan bağımsızdır.** Başka bir ifadeyle, projenizin belirli bir .NET platformunu hedeflemesi gerek değildir. Çözümleyiciler, hem hem de , ve gibi önceki .NET sürümlerini `net5.0` hedef alan projeler için `netcoreapp` `netstandard` `net472` çalışır.

Birinci taraf .NET çözümleyicilerini etkinleştirmek veya yüklemek için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- **.NET SDK'dan** etkinleştir: Visual Studio 2019 16.8 ve .NET 5.0'dan başlayarak, bu çözümleyiciler [.NET SDK'sı ile birlikte gelir.](/dotnet/fundamentals/code-analysis/overview) .NET 5.0 veya sonraki bir 5.0'a yönelik projeler için analiz varsayılan olarak etkindir. MSBUILD [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) özelliğini olarak ayarerek önceki .NET sürümlerini hedef alan projelerde kod analizini `true` etkinleştirebilirsiniz. ayrıca olarak ayararak projeniz için kod analizini devre dışı `EnableNETAnalyzers` `false` abilirsiniz.

- **NuGet** paketi olarak yükleme: .NET 5+ SDK'ya taşımak istemiyorsanız veya NuGet paket tabanlı bir model tercih ediyorsanız çözümleyiciler, `Microsoft.CodeAnalysis.NetAnalyzers` [Visual Studio](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) 2019'daki NuGet paketinde de kullanılabilir.  isteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edersiniz. 2017'Visual Studio, bunun yerine en son `2.9.x` `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet yükleyin.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)

> [!NOTE]
> Mümkün olduğunda, çözümleyicileri .NET SDK'sı yerine NuGet `Microsoft.CodeAnalysis.NetAnalyzers` [etkinleştirmeniz](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)önerilir. .NET SDK'dan çözümleyicilerin etkinleştirilmesi, SDK'yı güncelleştirince çözümleyici hata düzeltmelerini ve yeni çözümleyicileri otomatik olarak alanın. Yeni NuGet en son hata düzeltmelerini her NuGet paketi güncelleştirmeniz gerekir. NuGet paketi daha sık güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod çözümleyicilere genel bakış](roslyn-analyzers-overview.md)
- [Kod çözümleyicilerini Visual Studio](use-roslyn-analyzers.md)
- [Eski analizden .NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
