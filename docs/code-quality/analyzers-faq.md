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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800529"
---
# <a name="code-analysis-faq"></a>Kod Analizi hakkında SSS

Bu sayfa, Visual Studio 'da .NET Compiler Platform tabanlı kod analizi hakkında sık sorulan bazı soruların yanıtlarını içerir.

## <a name="code-analysis-versus-editorconfig"></a>Kod Analizi ve EditorConfig karşılaştırması

**S**: kod stilini denetlemek için kod analizini veya editorconfig 'i kullanmalıdır mi?

Y **: kod** Analizi ve editorconfig dosyaları el ile çalışır. [Bir EditorConfig dosyasında](/dotnet/fundamentals/code-analysis/code-style-rule-options) veya [metin düzenleyici seçenekleri](../ide/code-styles-and-code-cleanup.md) sayfasında kod stilleri tanımladığınızda aslında Visual Studio 'da yerleşik olarak bulunan kod Çözümleyicileri yapılandırılırsınız. EditorConfig dosyaları, çözümleyici kurallarını etkinleştirmek veya devre dışı bırakmak ve ayrıca NuGet çözümleyici paketlerini yapılandırmak için kullanılabilir.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig ve kural kümeleri

**S**: bir kural kümesi veya bir editorconfig dosyası kullanarak çözümleyicimi yapılandırmam gerekir mi?

Y **: kural** kümeleri ve editorconfig dosyaları birlikte bulunabilir ve her ikisi de Çözümleyicileri yapılandırmak için kullanılabilir. Hem EditorConfig dosyaları hem de kural kümeleri kuralları etkinleştirip devre dışı bırakmanızı ve bunların önem derecesini ayarlamanıza olanak sağlar.

Ancak, EditorConfig dosyaları kuralları yapılandırmak için ek yollar sunar:

- .NET kod kalitesi Çözümleyicileri için, EditorConfig dosyaları [hangi kod türlerini analiz edeceğinizi tanımlamanızı](/dotnet/fundamentals/code-analysis/code-quality-rule-options)sağlar.
- Visual Studio 'da yerleşik olarak bulunan .NET kod stili Çözümleyicileri için, EditorConfig dosyaları bir kod temeli için [tercih edilen kod stillerini tanımlamanıza](/dotnet/fundamentals/code-analysis/code-style-rule-options) olanak sağlar.

Kural kümelerine ve EditorConfig dosyalarına ek olarak, bazı çözümleyiciler C# ve VB derleyicileri için [ek dosyalar](../ide/build-actions.md#build-action-values) olarak işaretlenen metin dosyaları kullanılarak yapılandırılır.

> [!NOTE]
> - EditorConfig dosyaları yalnızca kuralları etkinleştirmek ve Visual Studio 2019 sürüm 16,3 ve üzeri önem derecesini ayarlamak için kullanılabilir.
> - EditorConfig dosyaları eski Analizi yapılandırmak için kullanılamaz, ancak kural kümeleri olabilir.

## <a name="code-analysis-in-ci-builds"></a>CI derlemeleri içinde kod analizi

**S:**.NET Compiler Platform tabanlı kod analizi sürekli tümleştirme (CI) derlemeleri üzerinde çalışır mı?

**A:** Evet. Bir NuGet paketinden yüklenmiş çözümleyiciler için, [](roslyn-analyzers-overview.md#build-errors)bu kurallar CI derlemesi sırasında dahil olmak üzere derleme zamanında uygulanır. CI derlemesinde kullanılan çözümleyiciler, hem kural kümelerinden hem de EditorConfig dosyalarından kural yapılandırmasını karşılar. Şu anda, Visual Studio yerleşik kod çözümleyicileri nuGet paketi olarak kullanılamaz ve bu nedenle bu kurallar CI derlemesinde zorlanmaz.

## <a name="ide-analyzers-versus-stylecop"></a>IDE çözümleyicileri ile StyleCop karşılaştırması

**S:** IDE kod çözümleyicileri Visual Studio StyleCop çözümleyicileri arasındaki fark nedir?

**A:** Visual Studio IDE, hem kod stili hem de kalite sorunlarını bulan yerleşik çözümleyiciler içerir. Bu kurallar, yeni dil özelliklerini kullanmaya ve kodunuzun bakımını geliştirmenize yardımcı olur. IDE çözümleyicileri her bir sürümle Visual Studio güncelleştirilir.

[StyleCop çözümleyicileri,](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) kodunuzda stil tutarlılığını kontrol eden bir NuGet paketi olarak yüklenmiş üçüncü taraf çözümleyicileridir. Genel olarak, StyleCop kuralları bir kod tabanı için bir stili diğerine önermeden kişisel tercihler ayarlamanızı sağlar.

## <a name="code-analyzers-versus-legacy-analysis"></a>Kod çözümleyicileri ile eski analiz karşılaştırması

**S:** Eski analiz ile .NET Compiler Platform arasındaki fark nedir?

**A:**.NET Compiler Platform tabanlı kod analizi, kaynak kodu gerçek zamanlı olarak ve derleme sırasında analiz ederken, eski analiz derleme tamamlandıktan sonra ikili dosyaları analiz eder. Daha fazla bilgi için [bkz. .NET Compiler Platform tabanlı analiz ile eski analiz karşılaştırması.](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

## <a name="fxcop-analyzers-versus-net-analyzers"></a>FxCop çözümleyicileri ile .NET çözümleyicileri karşılaştırması

**S:** FxCop çözümleyicileri ile .NET çözümleyicileri arasındaki fark nedir?

**Y:** FxCop çözümleyicileri ve .NET çözümleyicileri, FxCop CA kurallarının .NET Compiler Platform ("Roslyn") çözümleyicisi uygulamalarını ifade eder. Visual Studio 2019 16,8 ve .NET 5,0 öncesinde, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)olarak gönderilir. Visual Studio 2019 16,8 ve .NET 5,0 'den başlayarak, bu çözümleyiciler [.NET SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). Bunlar ayrıca `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)olarak da kullanılabilir. Lütfen [FxCop çözümleyicileri ' nden .net çözümleyicilerine geçiş](migrate-from-fxcop-analyzers-to-net-analyzers.md)yapmayı düşünün.

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir

**S**: projem uyarıları hata olarak değerlendirmek için Build seçeneğini kullanır. Eski analizden kaynak kodu çözümlemesine geçtikten sonra, tüm kod analizi uyarıları artık hata olarak görünür. Bunun nasıl önleyebilirim?

Y **: kod** Analizi uyarılarının hata olarak değerlendirilmesini engellemek için şu adımları izleyin:

  1. Aşağıdaki içeriğe sahip bir. props dosyası oluşturun:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Önceki adımda oluşturduğunuz. props dosyasını içeri aktarmak için. csproj veya. vbproj proje dosyanıza bir satır ekleyin. Bu satır, çözümleyici. props dosyalarını içeri aktararak herhangi bir satırdan önce yerleştirilmelidir. Örneğin,. props dosyanız CodeAnalysis. props olarak adlandırılmışsa:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Kod Analizi çözüm özellik sayfası

**S**: çözüm Için kod analizi Özellik sayfası nerede?

Y **: çözüm** düzeyindeki kod analizi Özellik sayfası, daha güvenilir paylaşılan özellik grubunun kullanım aşamasında kaldırılmıştır. Proje düzeyinde kod analizini yönetmek için, kod analizi Özellik sayfası hala kullanılabilir. (Yönetilen projeler için kural yapılandırması için RuleSets 'ten EditorConfig 'e geçiş de öneriyoruz.)  Bir çözüm ya da depodaki birden çok/tüm projede kural kümelerini paylaştırmak için, paylaşılan bir props/targets dosyasında veya *Dizin. props/Directory. targets* dosyasında [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) özelliği ile bir özellik grubu tanımlamayı öneririz. Tüm projeleriniz tarafından içeri aktarılan böyle bir ortak props veya hedefiniz yoksa, bu tür bir özellik grubunu bir [Dizin. props veya bir dizin. targets dosyasına](../msbuild/customize-your-build.md) eklemeyi göz önünde bulundurmanız gerekir. Bu, dizinde veya alt dizinlerinde tanımlanan tüm proje dosyalarına otomatik olarak içeri aktarılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyicilere genel bakış](roslyn-analyzers-overview.md)
- [EditorConfig için .NET kodlama kuralı ayarları](/dotnet/fundamentals/code-analysis/code-style-rule-options)