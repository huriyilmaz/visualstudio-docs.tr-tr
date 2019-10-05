---
title: FxCop Çözümleyicisi kural kümeleri
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974701"
---
# <a name="rule-sets-for-analyzer-packages"></a>Çözümleyici paketleri için kural kümeleri

Önceden tanımlanmış kural kümeleri, bazı NuGet çözümleyici paketlerine dahildir. Örneğin, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet çözümleyici paketine (sürüm 2.6.2 Critical ' den başlayarak) dahil edilen kural kümeleri, güvenlik, adlandırma veya performans gibi kategorilerine göre kuralları etkinleştirir veya devre dışı bırakır. Kural kümelerinin kullanılması, yalnızca belirli bir kural kategorisiyle ilgili olan kural ihlallerini hızlıca görmeyi kolaylaştırır.

Bir kural kümesi, hedeflenen sorunları ve belirli koşulları belirleyen kod analizi kurallarının bir gruplandırmasıdır. Kural kümeleri kuralları etkinleştirmenizi veya devre dışı bırakmanızı ve tek tek kural ihlalleri için önem derecesini ayarlamanıza olanak sağlar. FxCop Çözümleyicisi NuGet paketi aşağıdaki kural kategorileri için önceden tanımlanmış kural kümelerini içerir:

- tasarlama
- belgeler
- bakım
- adlandırma
- performans
- güvenilirlik
- güvenlik
- kullanım

Eski "FxCop" analizinden .NET Compiler Platform tabanlı kod çözümlemesine geçiş yapıyorsanız, bu kural kümeleri, [daha önce kullandığınız](rule-set-reference.md)şekilde benzer kural yapılandırmalarının kullanılmasına devam etmeyi sağlar.

## <a name="use-analyzer-package-rule-sets"></a>Çözümleyici paketi kural kümelerini kullanma

[NuGet Çözümleyicisi paketini](install-roslyn-analyzers.md)yükledikten sonra, *RuleSets* dizininde önceden tanımlanmış kural kümesini bulun. Örneğin, `Microsoft.CodeAnalysis.FxCopAnalyzers` çözümleyici paketine başvurdıysanız, *RuleSets* dizinini *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*adresinde bulabilirsiniz. Buradan, bir veya daha fazla RuleSets 'i kopyalayın ve bunları Visual Studio projenizi içeren dizine yapıştırın veya doğrudan **Çözüm Gezgini**.

Ayrıca, [önceden tanımlanmış bir kural kümesini](how-to-create-a-custom-rule-set.md) tercih etmeniz için özelleştirebilirsiniz. Örneğin, bir veya daha fazla kuralın önem derecesini değiştirerek ihlallerin **hata listesi**hata veya uyarı olarak görünmesini sağlayabilirsiniz.

## <a name="set-the-active-rule-set"></a>Etkin kural kümesini ayarla

Etkin kural kümesini ayarlama işlemi, .NET Core/. NET Standard projeniz veya .NET Framework projeniz olmasına bağlı olarak biraz farklıdır.

### <a name="net-core"></a>.NET Core

Bir kuralı, .NET Core veya .NET Standard projelerinde analiz için etkin kural kümesini ayarlamak için, **CodeAnalysisRuleSet** özelliğini proje dosyanıza el ile ekleyin. Örneğin, aşağıdaki kod parçacığı etkin kural kümesi olarak `HelloWorld.ruleset` ' ı ayarlar.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Bir kuralı .NET Framework projelerinde analiz için etkin kural kümesini ayarlamak için:

- **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' i seçin.

- Proje özelliği sayfalarında **Kod Analizi** sekmesini seçin.

::: moniker range="vs-2017"

- **Bu kural kümesini Çalıştır**' ın altında, **Araştır**' ı seçin ve ardından proje dizinine kopyaladığınız istenen kural kümesini seçin.

::: moniker-end

::: moniker range=">=vs-2019"

- **Etkin kurallar**altında, **Araştır**' ı seçin ve ardından proje dizinine kopyaladığınız istenen kural kümesini seçin.

::: moniker-end

   Şimdi yalnızca seçili kural kümesinde etkinleştirilen kuralların kural ihlallerini görürsünüz.

## <a name="available-rule-sets"></a>Kullanılabilir kural kümeleri

Önceden tanımlı çözümleyici kural kümeleri, @ no__t-0one paketindeki tüm kuralları etkileyen, bunların tümünü devre dışı bırakan ve her kuralın varsayılan önem derecesine ve etkinleştirme ayarlarına bir tane veren üç RuleSet içerir:

- AllRulesEnabled. RuleSet
- Allkuraldevre dışı. RuleSet
- Allkurallarını varsayılan. RuleSet

Ayrıca, paketteki her bir kural kategorisi için performans veya güvenlik gibi iki kural kümesi vardır. Bir kural kümesi kategori için tüm kurallara izin verir ve bir kural kümesi, kategorideki her bir kural için varsayılan önem derecesini ve etkinleştirme ayarlarını kabul eder.

[Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Çözümleyicisi paketi aşağıdaki kategorilerin kural kümelerini içerir:

- tasarlama
- belgeler
- bakım
- adlandırma
- performans
- güvenilirlik
- güvenlik
- kullanım

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler SSS](analyzers-faq.md)
- [.NET Compiler Platform çözümleyicilerine genel bakış](roslyn-analyzers-overview.md)
- [Çözümleyicileri yükleiciler](install-roslyn-analyzers.md)
- [Çözümleyicileri yapılandırma](use-roslyn-analyzers.md)
- [Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma](using-rule-sets-to-group-code-analysis-rules.md)
