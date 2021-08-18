---
title: Kod analizi kural kümeleri
ms.date: 07/23/2021
description: Visual Studio kodu analizinde yerleşik ve özelleştirilmiş kural kümeleri hakkında bilgi edinin. Bkz. dosyalardaki kural kümelerini belirtme ve projelerdeki kural kümelerini yapılandırma.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122078"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma

Visual Studio ' de kod analizini yapılandırdığınızda, yerleşik *kural kümeleri* listesinden seçim yapabilirsiniz. Kural kümesi, hedeflenen sorunları ve bu proje için belirli koşulları belirleyen kod analizi kurallarının bir gruplandırmasıdır. Örneğin, genel kullanıma açık API 'Ler için kodu taramak üzere tasarlanan bir kural kümesi uygulayabilirsiniz. Tüm kullanılabilir kuralları içeren bir kural kümesi de uygulayabilirsiniz.

Kural ekleyerek veya silerek veya **hata listesi** kural kümesi özellikleri ' ni uyarı veya hata olarak görünecek şekilde değiştirerek bir kural kümesini özelleştirebilirsiniz. Özelleştirilmiş kural kümeleri, belirli bir geliştirme ortamınız gereksinimini karşılayamıyor. Bir kural kümesini özelleştirdiğinizde, kural kümesi Düzenleyicisi, işlem sırasında size yardımcı olmak için arama ve filtreleme araçları sağlar.

Kural kümeleri, [yönetilen kod analizi](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [yönetilen kodun eski Analizi](how-to-configure-code-analysis-for-a-managed-code-project.md)ve [C++ kod analizi](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)için kullanılabilir.

>[!NOTE]
> Visual Studio 2019 sürüm 16,3 ' den başlayarak, .net kaynak kodu analizine yönelik kuralları yapılandırmak için editorconfig dosyalarını kullanabilirsiniz, ancak eski analize uygulanmaz. Daha fazla bilgi için SSS içindeki [Editorconfig ve kural kümeleri](../code-quality/analyzers-faq.yml) bölümüne bakın.

## <a name="rule-set-format"></a>Kural kümesi biçimi

Bir kural kümesi bir *. RuleSet* dosyasında XML biçiminde belirtilir. Bir KIMLIK ve bir *eylemden* oluşan kurallar, DOSYADAKI çözümleyici kimliğine ve ad alanına göre gruplandırılır.

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

bir projenin kural kümesi, Visual Studio proje dosyasındaki **codeanalysisruleset** özelliği tarafından belirtilir. Örnek:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)