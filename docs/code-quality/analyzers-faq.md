---
title: EditorConfig ve çözümleyiciler
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573254"
---
# <a name="code-analysis-faq"></a>Kod Analizi hakkında SSS

Bu sayfa, Visual Studio 'da .NET Compiler Platform tabanlı kod analizi hakkında sık sorulan bazı soruların yanıtlarını içerir.

## <a name="code-analysis-versus-editorconfig"></a>Kod Analizi ve EditorConfig karşılaştırması

**S**: kod stilini denetlemek için kod analizini veya editorconfig 'i kullanmalıdır mi?

Y **: kod**Analizi ve editorconfig dosyaları el ile çalışır. [Bir EditorConfig dosyasında](../ide/editorconfig-code-style-settings-reference.md) veya [metin düzenleyici seçenekleri](../ide/code-styles-and-code-cleanup.md) sayfasında kod stilleri tanımladığınızda aslında Visual Studio 'da yerleşik olarak bulunan kod Çözümleyicileri yapılandırılırsınız. EditorConfig dosyaları, çözümleyici kurallarını etkinleştirmek veya devre dışı bırakmak ve [FxCop çözümleyicileri](configure-fxcop-analyzers.md)gibi bazı NuGet çözümleyici paketlerini yapılandırmak için kullanılabilir.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig ve kural kümeleri

**S**: bir kural kümesi veya bir editorconfig dosyası kullanarak çözümleyicimi yapılandırmam gerekir mi?

Y **: kural**kümeleri ve editorconfig dosyaları birlikte bulunabilir ve her ikisi de Çözümleyicileri yapılandırmak için kullanılabilir. Hem EditorConfig dosyaları hem de kural kümeleri kuralları etkinleştirip devre dışı bırakmanızı ve bunların önem derecesini ayarlamanıza olanak sağlar.

Ancak, EditorConfig dosyaları kuralları yapılandırmak için ek yollar sunar:

- FxCop çözümleyicileri için, EditorConfig dosyaları [hangi kod türlerini analiz edeceğinizi tanımlamanızı](fxcop-analyzer-options.md)sağlar.
- Visual Studio 'da yerleşik olarak bulunan kod stili Çözümleyicileri için, EditorConfig dosyaları bir kod temeli için [tercih edilen kod stillerini tanımlamanıza](../ide/editorconfig-code-style-settings-reference.md) olanak sağlar.

Kural kümelerine ve EditorConfig dosyalarına ek olarak, bazı çözümleyiciler, C# ve vb derleyicileri için [ek dosyalar](../ide/build-actions.md#build-action-values) olarak işaretlenen metin dosyaları kullanılarak yapılandırılır.

> [!NOTE]
> - EditorConfig dosyaları yalnızca kuralları etkinleştirmek ve Visual Studio 2019 sürüm 16,3 ve üzeri önem derecesini ayarlamak için kullanılabilir.
> - EditorConfig dosyaları eski Analizi yapılandırmak için kullanılamaz, ancak kural kümeleri olabilir.

## <a name="code-analysis-in-ci-builds"></a>CI Derlemeleriyle kod analizi

**S**: .net Compiler platform tabanlı kod analizi sürekli TÜMLEŞTIRME (CI) Derlemeleriyle çalışıyor mu?

**Y**: Evet. Bir NuGet paketinden yüklenen çözümleyiciler için, bu kurallar bir CI derlemesi de dahil olmak üzere [derleme zamanında zorlanır](roslyn-analyzers-overview.md#build-errors). CI 'de kullanılan çözümleyiciler, kural kümelerinden ve EditorConfig dosyalarından gelen kural yapılandırmasına göre oluşturulur. Şu anda, Visual Studio 'da yerleşik olarak bulunan kod Çözümleyicileri bir NuGet paketi olarak kullanılamaz ve bu nedenle bu kurallar bir CI derlemesinde öngörülenebilir değildir.

## <a name="ide-analyzers-versus-stylecop"></a>IDE Çözümleyicileri ve StyleCop karşılaştırması

**S**: VISUAL Studio IDE kod Çözümleyicileri ve StyleCop Çözümleyicileri arasındaki fark nedir?

Y **: Visual**Studio IDE, hem kod stili hem de kalite sorunlarına yönelik yerleşik çözümleyiciler içerir. Bu kurallar, sunulan yeni dil özelliklerini kullanmanıza ve kodunuzun bakımlılığını iyileştirmenize yardımcı olur. IDE Çözümleyicileri her bir Visual Studio sürümüyle sürekli olarak güncelleştirilir.

[StyleCop Çözümleyicileri](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) , kodunuzda stil tutarlılığını denetleyen bir NuGet paketi olarak yüklenen üçüncü taraf Çözümleyicileri. Genel olarak, StyleCop kuralları bir kod tabanı için kişisel tercihlerinizi, başka bir stil önermeksizin ayarlamanıza olanak sağlar.

## <a name="code-analyzers-versus-legacy-analysis"></a>Kod Çözümleyicileri ve eski analizler

**S**: eski analiz ve .net Compiler platform tabanlı kod analizi arasındaki fark nedir?

Y **: .net Compiler platform**tabanlı kod analizi, kaynak kodu gerçek zamanlı ve derleme sırasında analiz ederken, eski analiz derleme tamamlandıktan sonra ikili dosyaları analiz eder. Daha fazla bilgi için, bkz. [.net Compiler platform tabanlı analizler, eski analizler](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) ve [FxCop çözümleyicileri hakkında SSS](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir

**S**: projem uyarıları hata olarak değerlendirmek için Build seçeneğini kullanır. Eski analizden kaynak kodu çözümlemesine geçtikten sonra, tüm kod analizi uyarıları artık hata olarak görünür. Bunun nasıl önleyebilirim?

Y **: kod**Analizi uyarılarının hata olarak değerlendirilmesini engellemek için şu adımları izleyin:

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

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler genel bakış](roslyn-analyzers-overview.md)
- [Kodlama kuralı ayarlarına EditorConfig için .NET](../ide/editorconfig-code-style-settings-reference.md)
