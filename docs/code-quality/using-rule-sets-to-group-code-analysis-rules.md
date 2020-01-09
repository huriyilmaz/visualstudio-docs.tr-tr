---
title: Kod analizi kural kümeleri
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a49f208fe3c60dfb8b9e20c83675cc43f1efb1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587179"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma

Visual Studio 'da Kod analizini yapılandırdığınızda, yerleşik *kural kümeleri*listesinden seçim yapabilirsiniz. Kural kümesi, hedeflenen sorunları ve bu proje için belirli koşulları belirleyen kod analizi kurallarının bir gruplandırmasıdır. Örneğin, genel kullanıma açık API 'Ler için kodu taramak üzere tasarlanan bir kural kümesi uygulayabilirsiniz. Tüm kullanılabilir kuralları içeren bir kural kümesi de uygulayabilirsiniz.

Kural ekleyerek veya silerek veya **hata listesi**kural kümesi özellikleri ' ni uyarı veya hata olarak görünecek şekilde değiştirerek bir kural kümesini özelleştirebilirsiniz. Özelleştirilmiş kural kümeleri, belirli bir geliştirme ortamınız gereksinimini karşılayamıyor. Bir kural kümesini özelleştirdiğinizde, kural kümesi Düzenleyicisi, işlem sırasında size yardımcı olmak için arama ve filtreleme araçları sağlar.

Kural kümeleri, [yönetilen kod analizi](analyzer-rule-sets.md), [yönetilen kodun eski Analizi](how-to-configure-code-analysis-for-a-managed-code-project.md)ve [ C++ kod analizi](using-rule-sets-to-specify-the-cpp-rules-to-run.md)için kullanılabilir.

## <a name="rule-set-format"></a>Kural kümesi biçimi

Bir kural kümesi bir *. RuleSet* dosyasında XML biçiminde belirtilir. Bir KIMLIK ve bir *eylemden*oluşan kurallar, DOSYADAKI çözümleyici kimliğine ve ad alanına göre gruplandırılır.

Bir *. RuleSet* dosyasının IÇERIĞI bu XML 'e benzer şekilde görünür:

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
> Grafik **kural kümesi düzenleyicisinde** el ile olandan [bir kural kümesini düzenlemek](../code-quality/working-in-the-code-analysis-rule-set-editor.md) daha kolay.

## <a name="specify-a-rule-set-for-a-project"></a>Bir proje için kural kümesi belirtme

Bir projenin kural kümesi, Visual Studio proje dosyasındaki **CodeAnalysisRuleSet** özelliği tarafından belirtilir. Örneğin:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
