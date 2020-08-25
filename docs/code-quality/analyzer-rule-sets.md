---
title: FxCop Çözümleyicisi kural kümeleri ve editorconfig dosyaları
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b99bb08c82725f19f7985a97656edf65f112d5
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800222"
---
# <a name="enable-a-category-of-rules"></a>Kural kategorisini etkinleştirme

Çözümleyici paketleri, güvenlik veya tasarım kuralları gibi bir kural kategorisini etkinleştirmeyi hızlı ve kolay hale getirmek için önceden tanımlanmış [Editorconfig](use-roslyn-analyzers.md#rule-severity) ve [kural kümesi](using-rule-sets-to-group-code-analysis-rules.md) dosyalarını içerebilir. [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet çözümleyici paketi, her iki kural kümesini (sürüm 2.6.2 Critical 'den başlayarak) ve editorconfig dosyalarını (sürüm 'nın 2.9.5 sürümüyle ' den başlayarak) içerir. Belirli bir kural kategorisini etkinleştirerek, hedeflenen sorunları ve belirli koşulları belirleyebilirsiniz.

> [!NOTE]
> Visual Studio 2019 sürüm 16,3 ' den başlayarak, çözümleyici kurallarını etkinleştirmek ve bir EditorConfig dosyası kullanarak önem derecesi ayarlamak desteklenir.

FxCop Çözümleyicisi NuGet paketi aşağıdaki kural kategorileri için önceden tanımlanmış kural kümelerini ve EditorConfig dosyalarını içerir:

- Tüm kurallar
- Veri akışı
- Tasarım
- Belgeler
- Genelleştirme
- Birlikte çalışabilirlik
- Bakım
- Adlandırma
- Performans
- FxCop 'den
- Güvenilirlik
- Güvenlik
- Kullanım

Bu kural kategorilerinin her biri bir EditorConfig veya kural kümesi dosyasına sahiptir:

- Kategorideki tüm kuralları etkinleştir (ve diğer tüm kuralları devre dışı bırak)
- Her kuralın varsayılan önem derecesini ve etkinleştirme ayarını kullanın (ve diğer tüm kuralları devre dışı bırakın)

> [!TIP]
> "Tüm kurallar" kategorisinin tüm kuralları devre dışı bırakmak için ek bir EditorConfig veya kural kümesi dosyası vardır. Bir projedeki hiçbir çözümleyici uyarılarından veya hatalarından kurtulmak için bu dosyayı kullanın.

> [!TIP]
> Eski "FxCop" analizinden .NET Compiler Platform tabanlı kod çözümlemesine geçiş yapıyorsanız, EditorConfig ve kural kümesi dosyaları, [daha önce kullandığınız](rule-set-reference.md)şekilde benzer kural yapılandırmalarını kullanmaya devam edebilmeniz için izin sağlar.

## <a name="predefined-editorconfig-files"></a>Önceden tanımlanmış EditorConfig dosyaları

Microsoft. CodeAnalysis. Fxcopçözümleyiciler çözümleyici paketi için önceden tanımlanmış EditorConfig dosyaları *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig* dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için EditorConfig dosyası *% USERPROFILE% \\ . Nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \Editorconfig\securityrulesenabled \\ . editorconfig*konumunda bulunur.

Seçilen. editorconfig dosyasını projenizin kök dizinine kopyalayın.

## <a name="predefined-rule-sets"></a>Önceden tanımlanmış kural kümeleri

Microsoft. CodeAnalysis. Fxcopçözümleyiciler çözümleyici paketi için önceden tanımlanmış kural kümesi dosyaları *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets* dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için kural kümesi dosyası *% USERPROFILE% \\ . Nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \Rulesets\securityrulesenabled.exe*konumunda bulunur.

Bir veya daha fazla kural kümesini kopyalayın ve Visual Studio projenizi içeren dizine veya doğrudan **Çözüm Gezgini**yapıştırın.

Ayrıca, [önceden tanımlanmış bir kural kümesini](how-to-create-a-custom-rule-set.md) tercih etmeniz için özelleştirebilirsiniz. Örneğin, bir veya daha fazla kuralın önem derecesini değiştirerek ihlallerin **hata listesi**hata veya uyarı olarak görünmesini sağlayabilirsiniz.

### <a name="set-the-active-rule-set"></a>Etkin kural kümesini ayarla

Etkin kural kümesini ayarlama işlemi, .NET Core/. NET Standard projeniz veya .NET Framework projeniz olmasına bağlı olarak biraz farklıdır.

#### <a name="net-core"></a>.NET Core

Bir kuralı, .NET Core veya .NET Standard projelerinde analiz için etkin kural kümesini ayarlamak için, **CodeAnalysisRuleSet** özelliğini proje dosyanıza el ile ekleyin. Örneğin, aşağıdaki kod parçacığı `HelloWorld.ruleset` etkin kural kümesi olarak ayarlanır.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler hakkında SSS](analyzers-faq.md)
- [.NET Compiler Platform çözümleyicilerine genel bakış](roslyn-analyzers-overview.md)
- [Çözümleyicileri yükleiciler](install-roslyn-analyzers.md)
- [Çözümleyicileri yapılandırma](use-roslyn-analyzers.md)
- [Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma](using-rule-sets-to-group-code-analysis-rules.md)
