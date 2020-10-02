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
ms.openlocfilehash: 47019ecd01a4ad432a853a7f1a4f7d7112be163c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659211"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma

Visual Studio 'da Kod analizini yapılandırdığınızda, yerleşik *kural kümeleri*listesinden seçim yapabilirsiniz. Kural kümesi, hedeflenen sorunları ve bu proje için belirli koşulları belirleyen kod analizi kurallarının bir gruplandırmasıdır. Örneğin, genel kullanıma açık API 'Ler için kodu taramak üzere tasarlanan bir kural kümesi uygulayabilirsiniz. Tüm kullanılabilir kuralları içeren bir kural kümesi de uygulayabilirsiniz.

Kural ekleyerek veya silerek veya **hata listesi**kural kümesi özellikleri ' ni uyarı veya hata olarak görünecek şekilde değiştirerek bir kural kümesini özelleştirebilirsiniz. Özelleştirilmiş kural kümeleri, belirli bir geliştirme ortamınız gereksinimini karşılayamıyor. Bir kural kümesini özelleştirdiğinizde, kural kümesi Düzenleyicisi, işlem sırasında size yardımcı olmak için arama ve filtreleme araçları sağlar.

Kural kümeleri, [yönetilen kod analizi](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [yönetilen kodun eski Analizi](how-to-configure-code-analysis-for-a-managed-code-project.md)ve [C++ kod analizi](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)için kullanılabilir.

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

Bir projenin kural kümesi, Visual Studio proje dosyasındaki **CodeAnalysisRuleSet** özelliği tarafından belirtilir. Örnek:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
