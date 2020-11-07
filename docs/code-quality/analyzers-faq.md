---
title: EditorConfig ve çözümleyiciler
ms.date: 03/11/2019
description: Visual Studio 'da .NET Compiler Platform tabanlı kod analizi hakkında bilgi edinin. Bkz. EditorConfig dosyaları, kural kümeleri ve diğer konular hakkında soruların yanıtları.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20d566937286743a684ecce2ff54ff2cafe4b3a4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348406"
---
# <a name="code-analysis-faq"></a>Kod Analizi hakkında SSS

Bu sayfa, Visual Studio 'da .NET Compiler Platform tabanlı kod analizi hakkında sık sorulan bazı soruların yanıtlarını içerir.

## <a name="code-analysis-versus-editorconfig"></a>Kod Analizi ve EditorConfig karşılaştırması

**S** : kod stilini denetlemek için kod analizini veya editorconfig 'i kullanmalıdır mi?

Y **: kod** Analizi ve editorconfig dosyaları el ile çalışır. [Bir EditorConfig dosyasında](/dotnet/fundamentals/code-analysis/code-style-rule-options) veya [metin düzenleyici seçenekleri](../ide/code-styles-and-code-cleanup.md) sayfasında kod stilleri tanımladığınızda aslında Visual Studio 'da yerleşik olarak bulunan kod Çözümleyicileri yapılandırılırsınız. EditorConfig dosyaları, çözümleyici kurallarını etkinleştirmek veya devre dışı bırakmak ve ayrıca NuGet çözümleyici paketlerini yapılandırmak için kullanılabilir.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig ve kural kümeleri

**S** : bir kural kümesi veya bir editorconfig dosyası kullanarak çözümleyicimi yapılandırmam gerekir mi?

Y **: kural** kümeleri ve editorconfig dosyaları birlikte bulunabilir ve her ikisi de Çözümleyicileri yapılandırmak için kullanılabilir. Hem EditorConfig dosyaları hem de kural kümeleri kuralları etkinleştirip devre dışı bırakmanızı ve bunların önem derecesini ayarlamanıza olanak sağlar.

Ancak, EditorConfig dosyaları kuralları yapılandırmak için ek yollar sunar:

- .NET kod kalitesi Çözümleyicileri için, EditorConfig dosyaları [hangi kod türlerini analiz edeceğinizi tanımlamanızı](/dotnet/fundamentals/code-analysis/code-quality-rule-options)sağlar.
- Visual Studio 'da yerleşik olarak bulunan .NET kod stili Çözümleyicileri için, EditorConfig dosyaları bir kod temeli için [tercih edilen kod stillerini tanımlamanıza](/dotnet/fundamentals/code-analysis/code-style-rule-options) olanak sağlar.

Kural kümelerine ve EditorConfig dosyalarına ek olarak, bazı çözümleyiciler C# ve VB derleyicileri için [ek dosyalar](../ide/build-actions.md#build-action-values) olarak işaretlenen metin dosyaları kullanılarak yapılandırılır.

> [!NOTE]
> - EditorConfig dosyaları yalnızca kuralları etkinleştirmek ve Visual Studio 2019 sürüm 16,3 ve üzeri önem derecesini ayarlamak için kullanılabilir.
> - EditorConfig dosyaları eski Analizi yapılandırmak için kullanılamaz, ancak kural kümeleri olabilir.

## <a name="code-analysis-in-ci-builds"></a>CI Derlemeleriyle kod analizi

**S** : .net Compiler platform tabanlı kod analizi sürekli TÜMLEŞTIRME (CI) Derlemeleriyle çalışıyor mu?

Y **: Evet**. Bir NuGet paketinden yüklenen çözümleyiciler için, bu kurallar bir CI derlemesi de dahil olmak üzere [derleme zamanında zorlanır](roslyn-analyzers-overview.md#build-errors). CI 'de kullanılan çözümleyiciler, kural kümelerinden ve EditorConfig dosyalarından gelen kural yapılandırmasına göre oluşturulur. Şu anda, Visual Studio 'da yerleşik olarak bulunan kod Çözümleyicileri bir NuGet paketi olarak kullanılamaz ve bu nedenle bu kurallar bir CI derlemesinde öngörülenebilir değildir.

## <a name="ide-analyzers-versus-stylecop"></a>IDE Çözümleyicileri ve StyleCop karşılaştırması

**S** : VISUAL Studio IDE kod Çözümleyicileri ve StyleCop Çözümleyicileri arasındaki fark nedir?

Y **: Visual** Studio IDE, hem kod stili hem de kalite sorunlarına yönelik yerleşik çözümleyiciler içerir. Bu kurallar, sunulan yeni dil özelliklerini kullanmanıza ve kodunuzun bakımlılığını iyileştirmenize yardımcı olur. IDE Çözümleyicileri her bir Visual Studio sürümüyle sürekli olarak güncelleştirilir.

[StyleCop Çözümleyicileri](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) , kodunuzda stil tutarlılığını denetleyen bir NuGet paketi olarak yüklenen üçüncü taraf Çözümleyicileri. Genel olarak, StyleCop kuralları bir kod tabanı için kişisel tercihlerinizi, başka bir stil önermeksizin ayarlamanıza olanak sağlar.

## <a name="code-analyzers-versus-legacy-analysis"></a>Kod Çözümleyicileri ve eski analizler

**S** : eski analiz ve .net Compiler platform tabanlı kod analizi arasındaki fark nedir?

Y **: .net Compiler platform** tabanlı kod analizi, kaynak kodu gerçek zamanlı ve derleme sırasında analiz ederken, eski analiz derleme tamamlandıktan sonra ikili dosyaları analiz eder. Daha fazla bilgi için bkz. [.net Compiler platform tabanlı analizler ve eski analizler](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers).

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir

**S** : projem uyarıları hata olarak değerlendirmek için Build seçeneğini kullanır. Eski analizden kaynak kodu çözümlemesine geçtikten sonra, tüm kod analizi uyarıları artık hata olarak görünür. Bunun nasıl önleyebilirim?

Y **: kod** Analizi uyarılarının hata olarak değerlendirilmesini engellemek için şu adımları izleyin:

  1. Aşağıdaki içeriğe sahip bir. props dosyası oluşturun:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Önceki adımda oluşturduğunuz. props dosyasını içeri aktarmak için. csproj veya. vbproj proje dosyanıza bir satır ekleyin. Bu satır, FxCop Çözümleyicisi. props dosyalarını içeri aktararak herhangi bir satırdan önce yerleştirilmelidir. Örneğin,. props dosyanız CodeAnalysis. props olarak adlandırılmışsa:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Kod Analizi çözüm özellik sayfası

**S** : çözüm Için kod analizi Özellik sayfası nerede?

Y **: çözüm** düzeyindeki kod analizi Özellik sayfası, daha güvenilir paylaşılan özellik grubunun kullanım aşamasında kaldırılmıştır. Proje düzeyinde kod analizini yönetmek için, kod analizi Özellik sayfası hala kullanılabilir. (Yönetilen projeler için kural yapılandırması için RuleSets 'ten EditorConfig 'e geçiş de öneriyoruz.)  Bir çözüm ya da depodaki birden çok/tüm projede kural kümelerini paylaştırmak için, paylaşılan bir props/targets dosyasında veya dizin. props/Directory. targets dosyasında CodeAnalysisRuleSet özelliği ile bir özellik grubu tanımlamayı öneririz. Tüm projelerinizi içeri aktardıkları böyle bir ortak props veya hedefiniz yoksa, bu [tür bir özellik grubunu bir dizin. props veya bir dizin. targets, dizinde veya alt dizinlerinde tanımlanan tüm proje dosyalarına otomatik olarak içeri aktarılan bir en üst düzey çözüm dizinine eklemeyi](../msbuild/customize-your-build.md)göz önünde bulundurmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler genel bakış](roslyn-analyzers-overview.md)
- [EditorConfig için .NET kodlama kuralı ayarları](/dotnet/fundamentals/code-analysis/code-style-rule-options)