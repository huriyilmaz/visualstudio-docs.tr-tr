---
title: Roslyn Çözümleyicileri kullanarak kod analizi
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: af237fbc3ce7bcf098cd47065ed18d1dfd7f20a2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975005"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>.NET Compiler Platform Code çözümleyicilerine genel bakış

.NET Compiler Platform ("Roslyn") Çözümleyicileri, kodunuzu stil, kalite ve bakım, tasarım ve diğer sorunlar için analiz eder. Visual Studio, siz yazarken C# veya Visual Basic kodunuzu çözümleyen yerleşik çözümleyiciler kümesini içerir. Bu yerleşik çözümleyiciler için tercihleri [metin düzenleyici seçenekleri](../ide/code-styles-and-code-cleanup.md) sayfasında veya bir [. editorconfig dosyasında](../ide/editorconfig-code-style-settings-reference.md)yapılandırırsınız. Ek Çözümleyicileri, Visual Studio uzantısı veya NuGet paketi olarak yükleyebilirsiniz.

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve **hata listesi** penceresinde raporlanır.

Birçok çözümleyici kuralı veya *tanılaması*, sorunu gidermek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* birlikte bulunabilir. Visual Studio 'da yerleşik olarak bulunan çözümleyici tanılamaları, ilişkili bir kod düzeltmesine sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/common-quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>.NET Compiler Platform tabanlı analizler ve eski analizler

.NET Compiler Platform ("Roslyn") kod analizi sonunda, yönetilen kod için [eski analizler](../code-quality/code-analysis-for-managed-code-overview.md) değiştirilir. Eski analiz kurallarının birçoğu .NET Compiler Platform tabanlı kod Çözümleyicileri olarak zaten yeniden yazıldı.

Eski analiz kuralı ihlalleri gibi .NET Compiler Platform tabanlı kod analizi ihlalleri, Visual Studio 'daki Hata Listesi penceresinde görünür. Ayrıca, .NET Compiler Platform tabanlı kod analizi ihlalleri, kod Düzenleyicisi 'nde, sorunlu kodun altında *dalgalı çizgiler* olarak da görünür. Dalgalı çizginin rengi kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#rule-severity) bağlıdır. Aşağıdaki ekran görüntüsünde, @ no__t-0one kırmızı, bir yeşil ve bir gri olmak üzere üç ihlal gösterilmektedir:

![Kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

.NET Compiler Platform tabanlı kod Çözümleyicileri, etkinleştirilirse eski analizler gibi derleme zamanında kodu analiz eder, ancak yazarken da canlı hale gelir. [Tam çözüm analizini](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis)etkinleştirirseniz kod Çözümleyicileri, düzenleyicide açık olmayan kod dosyalarının tasarım zamanı analizini de sağlar.

> [!TIP]
> Kod Çözümleyicileri içindeki derleme zamanı hataları ve uyarıları yalnızca çözümleyiciler bir NuGet paketi olarak yüklenirse gösterilir.

Yalnızca .NET Compiler Platform tabanlı kod Çözümleyicileri, eski analizler için de aynı tür sorunları rapor eder, ancak dosya veya projenizde ihlalin bir kısmını veya tümünü düzeltmenize olanak sağlar. Bu eylemlere *kod düzeltmeleri*denir. Kod düzeltmeleri IDE 'ye özgüdür; Visual Studio 'da, bunlar [hızlı eylemler](../ide/quick-actions.md)olarak uygulanır. Tüm çözümleyici tanılamaları ilişkili bir kod düzeltmesine sahip değildir.

> [!NOTE]
> Aşağıdaki UI seçenekleri yalnızca eski analizler için geçerlidir:
>
> - @No__t-1 ' i **Çözümle** **kodu analizi Çalıştır** menü seçeneği.
> - **Üzerinde Çalıştır** , projenin özellik sayfalarındaki **Kod Analizi** sekmesinde **oluşturulan kod** onay kutularından sonuçları oluşturur ve gizler.

Hata Listesi penceresinde kod Çözümleyicileri ve eski analizin ihlalleri arasında ayrım yapmak için **araç** sütununa bakın. Araç değeri **Çözüm Gezgini**içindeki çözümleyici derlemelerinden biriyle eşleşiyorsa (örneğin, **Microsoft. Codequality. çözümleyiciler**), Ihlal bir kod çözümleyicisinden gelir. Aksi takdirde, ihlalin eski analizler.

![Hata Listesi araç sütunu](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Bir proje dosyasındaki **RunCodeAnalysis** MSBuild özelliği yalnızca eski analiz için geçerlidir. Çözümleyiciler yüklerseniz, derleme sonrasında eski çözümlemenin çalıştırılmasını engellemek için **RunCodeAnalysis** öğesini proje dosyanızda **false** olarak ayarlayın.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketi ve VSıX uzantısı

.NET Compiler Platform Çözümleyicileri, bir NuGet paketi veya Visual Studio uzantısı olarak Visual Studio uzantısı aracılığıyla her proje için yüklenebilir. Bu iki çözümleyici [yükleme](../code-quality/install-roslyn-analyzers.md)yöntemi arasında bazı önemli davranış farklılıkları vardır.

### <a name="scope"></a>`Scope`

Çözümleyiciler Visual Studio uzantısı olarak yüklerseniz, çözüm düzeyinde Visual Studio 'nun tüm örneklerine uygulanır. Çözümleyicileri, tercih edilen yöntemi olan bir NuGet paketi olarak yüklerseniz, yalnızca NuGet paketinin yüklendiği proje için geçerlidir. Ekip ortamlarında, NuGet paketleri olarak yüklenen çözümleyiciler, o projede çalışan *tüm geliştiriciler* için kapsamdadır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı veya bir sürekli tümleştirme (CI) yapısının parçası olarak, derleme zamanında uygulanan kuralların uygulanmasını sağlamak için, Çözümleyicileri bir NuGet paketi olarak yükler. Çözümleyici uyarıları ve hataları, çözümleyiciler bir uzantı olarak yüklerseniz derleme raporunda gösterilmez.

Aşağıdaki ekran görüntüsünde, bir çözümleyici kuralı ihlali içeren bir proje oluşturmanın komut satırı derleme çıkışı gösterilmektedir:

![Kural ihlali ile MSBuild çıkışı](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural önem derecesi

Visual Studio uzantısı olarak yüklenen çözümleyicilerin kurallarının önem derecesini ayarlayamazsınız. [Kural önem derecesini](../code-quality/use-roslyn-analyzers.md#rule-severity)yapılandırmak için Çözümleyicileri bir NuGet paketi olarak yükler.

## <a name="categories"></a>Categories

Aşağıda, kodunuzun çözümlenmesine yardımcı olan farklı çözümleyiciler türleri verilmiştir:

- Microsoft 'un önerilen çözümleyiciler: [FxCop çözümleyicileri](../code-quality/fxcop-analyzers.yml)
- Visual Studio IDE Çözümleyicileri: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Üçüncü taraf Çözümleyicileri: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [roslynator](https://www.nuget.org/packages/Roslynator/), [xUnit Çözümleyicileri](https://www.nuget.org/packages/xunit.analyzers/), [sonar Çözümleyicisi](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri yüklemesi](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler SSS](analyzers-faq.md)
- [Kendi kod çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
