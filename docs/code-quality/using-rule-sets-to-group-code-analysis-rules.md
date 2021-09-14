---
title: Kod analizi kural kümeleri
ms.date: 07/23/2021
description: Kod analizinde yerleşik ve özelleştirilmiş kural kümeleri Visual Studio öğrenin. Dosyalarda kural kümelerini belirtmeye ve projelerde kural kümelerini yapılandırmaya bakın.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 856fd236959b8335ded1ff2007bc5a5d1dd29a90
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631803"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Kod analizi kurallarını grup etmek için kural kümelerini kullanma

Kod analizini bir Visual Studio, yerleşik kural kümeleri listesinden *seçebilirsiniz.* Kural kümesi, hedeflenen sorunları ve bu proje için belirli koşulları belirleyen bir kod analizi kuralları grubudur. Örneğin, genel kullanıma açık API'ler için kodu taramak üzere tasarlanmış bir kural kümesi uygulayabilirsiniz. Kullanılabilir tüm kuralları içeren bir kural kümesi de uygulayabilirsiniz.

Kural kümesi ekleyerek veya silerek ya da kural hatalarını Hata Listesinde uyarılar veya hatalar olarak görünecek şekilde değiştirerek bir kural **kümesi özelleştirebilirsiniz.** Özelleştirilmiş kural kümeleri, kendi geliştirme ortamınız için bir ihtiyacı karşılar. Bir kural kümesi özelleştirerek kural kümesi düzenleyicisi, işlemde size yardımcı olacak arama ve filtreleme araçları sağlar.

Kural kümeleri yönetilen kod [analizi, yönetilen](/dotnet/fundamentals/code-analysis/code-quality-rule-options) [kodun eski analizi ve](how-to-configure-code-analysis-for-a-managed-code-project.md) [C++ kod analizi için kullanılabilir.](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)

>[!NOTE]
> 2019 Visual Studio 16.3 sürümünden başlayarak, .NET kaynak kodu analizi kurallarını yapılandırmak için EditorConfig dosyalarını kullanabilirsiniz, ancak eski analizi yapılandırabilirsiniz. Daha fazla bilgi için [SSS bölümündeki EditorConfig ve kural](../code-quality/analyzers-faq.yml) kümeleri karşılaştırması bölümüne bakın.

## <a name="rule-set-format"></a>Kural kümesi biçimi

Bir kural kümesi bir *.ruleset* dosyasında XML biçiminde belirtilir. Bir kimlik ve eylemden oluşan *kurallar,* dosyada çözümleyici kimliğine ve ad alanına göre gruplandırılmıştır.

*Bir .ruleset dosyasının içeriği* şu XML'ye benzer:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Grafiksel Kural Kümesi [Düzenleyicisi'nde kural kümesi](../code-quality/working-in-the-code-analysis-rule-set-editor.md) düzenlemek el **ile düzenlemekten** daha kolaydır.

## <a name="specify-a-rule-set-for-a-project"></a>Proje için kural kümesi belirtme

Bir proje için kural kümesi, proje dosyasındaki **CodeAnalysisRuleSet** Visual Studio belirtilir. Örnek:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)