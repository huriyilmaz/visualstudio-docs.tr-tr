---
title: FxCop çözümleyicileri 'nden .NET çözümleyicilerine geçiş
ms.custom: SEO-VS-2020
description: FxCop çözümleyicileri ' nden .NET çözümleyicilerine nasıl geçiş yapılacağını öğrenin
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112249"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop çözümleyicileri 'nden .NET çözümleyicilerine geçiş

.NET Compiler Platform ("Roslyn") Çözümleyicileri kaynak analizi, yönetilen kod için [eski analizler](code-analysis-for-managed-code-overview.md) yerini alır. Eski analiz (FxCop) kurallarının birçoğu kaynak Çözümleyicileri olarak zaten yeniden yazıldı.

Visual Studio 2019 16,8 ve .NET 5,0 öncesinde, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)olarak gönderilir.

Visual Studio 2019 16,8 ve .NET 5,0 'den başlayarak, bu çözümleyiciler [.NET SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). Bunlar ayrıca `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)olarak da kullanılabilir. `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet paketi yakında kullanım dışı bırakılacak.

## <a name="migration-steps"></a>Geçiş adımları

Projenizi veya çözümünüzü .NET çözümleyicilerine geçirmek için lütfen aşağıdaki adımları izleyin `Microsoft.CodeAnalysis.FxCopAnalyzers` :

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`NuGet paketini kaldır

2. [.NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi](install-net-analyzers.md)

3. Ek kuralları etkinleştir: ile `Microsoft.CodeAnalysis.NetAnalyzers` karşılaştırıldığında çok daha fazla koruyucu `Microsoft.CodeAnalysis.FxCopAnalyzers` . Fxcopçözümleyiciler paketinin aksine, yalnızca [derleme uyarıları olarak varsayılan olarak etkinleştirilen](/dotnet/fundamentals/code-analysis/overview#enabled-rules)birkaç doğruluk kuralına sahiptir. [Analysismode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild özelliğini özelleştirerek [ek kurallara izin](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) verebilirsiniz. Örneğin, özelliğinin olarak ayarlanması, `AllEnabledByDefault` geçerli tüm CA kurallarının varsayılan olarak derleme uyarıları olarak etkinleştirecektir.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak kodu analizi ve eski analiz karşılaştırması](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Eski analizden .NET çözümleyiciler 'e geçiş](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET çözümleyicilerinin etkinleştirilmesi veya yüklenmesi](install-net-analyzers.md)
- [.NET Çözümleyicileri hakkında SSS](net-analyzers-faq.md)
- [.NET Çözümleyicileri yapılandırma](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
