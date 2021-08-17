---
title: FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme
ms.custom: SEO-VS-2020
description: FxCop çözümleyicilerinden .NET çözümleyicilere geçiş yapmayı öğrenin
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: b900c886703aeed3edb3ae069cbdbc3e5bceea11945ef6d8ba92fc85aa3c76b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363222"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme

.NET Compiler Platform ("Roslyn") çözümleyicileri tarafından yapılan kaynak analizi, yönetilen [kod için eski](code-analysis-for-managed-code-overview.md) analizin yerini alır. Eski analiz (FxCop) kurallarının çoğu zaten kaynak çözümleyiciler olarak yeniden yazılmıştır.

2019 Visual Studio 16.8 ve .NET 5.0'dan önce, bu çözümleyiciler NuGet `Microsoft.CodeAnalysis.FxCopAnalyzers` [olarak gönderildi.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)

2019 Visual Studio 16.8 ve .NET 5.0'dan başlayarak, bu çözümleyiciler [.NET SDK'sı ile birlikte gelir.](/dotnet/fundamentals/code-analysis/overview) .NET 5+ SDK'ya taşınmak istemiyorsanız veya NuGet paket tabanlı bir model tercih ediyorsanız çözümleyiciler' NuGet `Microsoft.CodeAnalysis.NetAnalyzers` [kullanılabilir.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) isteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edersiniz.

> [!NOTE]
> Birinci taraf .NET çözümleyicileri hedef platformdan bağımsızdır. Başka bir ifadeyle, projenizin belirli bir .NET platformunu hedeflemesi gerek değildir. Çözümleyiciler, hem hem de , ve gibi önceki .NET sürümlerini `net5.0` hedef alan projeler için `netcoreapp` `netstandard` `net472` çalışır.

## <a name="migration-steps"></a>Geçiş adımları

sürümünden `3.3.2` itibaren `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet paketi kullanım dışıdır. Projenizi veya çözümleyicilerinizi .NET çözümleyicilerinden geçirmek `Microsoft.CodeAnalysis.FxCopAnalyzers` için lütfen aşağıdaki adımları izleyin:

1. Paket `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet kaldırma

2. [.NET çözümleyicilerini etkinleştirin veya yükleyin.](install-net-analyzers.md) Projenizin hedef platformunu değiştirmek zorunda olmadığını unutmayın.

3. Ek kuralları etkinleştir: `Microsoft.CodeAnalysis.NetAnalyzers` ile karşılaştırıldığında çok daha tutucudur. `Microsoft.CodeAnalysis.FxCopAnalyzers` FxCopAnalyzers paketinin aksine, derleme uyarıları olarak varsayılan olarak etkin olan yalnızca [birkaç doğruluk kuralı vardır.](/dotnet/fundamentals/code-analysis/overview#enabled-rules) [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) [MSBuild](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) özelliğini özelleştirerek MSBuild etkinleştirabilirsiniz. Örneğin, özelliğini olarak ayarlayan `AllEnabledByDefault` tüm ilgili CA kuralları varsayılan olarak derleme uyarıları olarak etkinleştirildi.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak kodu analiziyle eski analiz karşılaştırması](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Eski analizden .NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET çözümleyicilerini etkinleştirme veya yükleme](install-net-analyzers.md)
- [.NET çözümleyicileri hakkında SSS](net-analyzers-faq.yml)
- [.NET çözümleyicilerini yapılandırma](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
