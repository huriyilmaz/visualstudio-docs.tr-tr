---
title: Roslyn Çözümleyicileri kullanarak kod analizi
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34225858e88f4ee969f0e51013bcdb04812d425f
ms.sourcegitcommit: a86ee68e3ec23869b6eaaf6c6b7946b1d9a88d01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77144765"
---
# <a name="overview-of-source-code-analyzers"></a>Kaynak kodu Çözümleyicileri 'ne genel bakış

.NET Compiler Platform ("Roslyn") kod Çözümleyicileri stil, kalite C# ve bakım, tasarım ve diğer sorunlar için veya Visual Basic kodunuzu inceler.

- Bazı çözümleyiciler, Visual Studio 'da yerleşik olarak bulunur. Bu çözümleyiciler için tanılama KIMLIĞI veya kodu ıdexxxx biçimindedir, örneğin, IDE0067. Bu yerleşik çözümleyiciler çoğu [kod stilini](../ide/code-styles-and-code-cleanup.md)inceler ve [metin düzenleyici seçenekleri sayfasında](../ide/code-styles-and-code-cleanup.md) veya bir [editorconfig dosyasında](../ide/editorconfig-code-style-settings-reference.md)tercihleri yapılandırabilirsiniz. Çeşitli yerleşik çözümleyiciler kod kalitesine bakar.

- NuGet paketi veya Visual Studio uzantısı olarak ek çözümleyiciler yükleyebilirsiniz. Örneğin:

  - [FxCop çözümleyicileri](../code-quality/install-fxcop-analyzers.md), Microsoft 'un önerilen kod kalitesi Çözümleyicileri
  - [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit Çözümleyicileri](https://www.nuget.org/packages/xunit.analyzers/)ve [sonar Çözümleyicisi](https://www.nuget.org/packages/SonarAnalyzer.CSharp/) gibi üçüncü taraf Çözümleyicileri

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

Birçok çözümleyici kuralı veya *tanılaması*, sorunu gidermek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* birlikte bulunabilir. Visual Studio 'da yerleşik olarak bulunan çözümleyici tanılamaları, ilişkili bir kod düzeltmesine sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/common-quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Kaynak kodu analizi ve eski analiz karşılaştırması

Roslyn çözümleyicilerine göre kaynak analizi, yönetilen kod için [eski Analizi](../code-quality/code-analysis-for-managed-code-overview.md) yerine koyar. Eski analiz kurallarının birçoğu zaten Roslyn kod Çözümleyicileri olarak yeniden yazıldı. .NET Core ve .NET Standard projeleri gibi daha yeni proje şablonları için eski analizler de kullanılamaz.

Eski analiz kuralı ihlallerine benzer şekilde, kaynak kodu çözümleme ihlalleri Visual Studio 'daki Hata Listesi penceresinde görüntülenir. Ayrıca, kaynak kodu çözümleme ihlalleri, kod Düzenleyicisi 'nde, sorunlu kodun altında *dalgalı çizgiler* olarak da görünür. Dalgalı çizginin rengi kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#rule-severity) bağlıdır. Aşağıdaki görüntüde, bir kırmızı, bir yeşil ve bir gri&mdash;üç ihlal gösterilmektedir:

![Visual Studio 'da kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Kod Çözümleyicileri, derleme zamanında kodu inceleyerek eski analizler gibi, ancak yazarken da canlı olur. [Tam çözüm analizini](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis)etkinleştirirseniz kod Çözümleyicileri, düzenleyicide açık olmayan kod dosyalarının tasarım zamanı analizini de sağlar.

> [!TIP]
> Kod Çözümleyicileri içindeki derleme zamanı hataları ve uyarıları yalnızca çözümleyiciler bir NuGet paketi olarak yüklenirse gösterilir. Yerleşik çözümleyiciler (örneğin, IDE0067 ve IDE0068) derleme sırasında hiçbir şekilde çalıştırılmadı.

Yalnızca Roslyn kod Çözümleyicileri, eski analizler tarafından aynı tür sorunları rapor etmez, ancak dosya veya projenizde ihlalin bir veya bütün tekrarlarını düzeltmenize olanak sağlar. Bu eylemlere *kod düzeltmeleri*denir. Kod düzeltmeleri IDE 'ye özgüdür; Visual Studio 'da, bunlar [hızlı eylemler](../ide/quick-actions.md)olarak uygulanır. Tüm çözümleyici tanılamaları ilişkili bir kod düzeltmesine sahip değildir.

> [!NOTE]
>  > **çalıştırma kodu analizini** **Çözümle** menü seçeneği yalnızca eski analizler için geçerlidir.

Hata Listesi kod Çözümleyicileri ve eski analizin ihlallerini birbirinden ayırt etmek için **araç** sütununa bakın. Araç değeri **Çözüm Gezgini**içindeki çözümleyici derlemelerinden biriyle eşleşiyorsa (örneğin, **Microsoft. Codequality. çözümleyiciler**), Ihlal bir kod çözümleyicisinden gelir. Aksi takdirde, ihlalin eski analizler.

![Hata Listesi araç sütunu](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Bir proje dosyasındaki **RunCodeAnalysis** MSBuild özelliği yalnızca eski analiz için geçerlidir. Çözümleyiciler yüklerseniz, derleme sonrasında eski çözümlemenin çalıştırılmasını engellemek için **RunCodeAnalysis** öğesini proje dosyanızda **false** olarak ayarlayın.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketi ve VSıX uzantısı

Roslyn kod Çözümleyicileri, bir NuGet paketi aracılığıyla proje başına yüklenebilir. Bazıları Visual Studio uzantısı olarak da kullanılabilir, bu durumda Visual Studio 'da açtığınız tüm çözümler için geçerlidir. Bu iki çözümleyici [yükleme](../code-quality/install-roslyn-analyzers.md)yöntemi arasında bazı önemli davranış farklılıkları vardır.

### <a name="scope"></a>Kapsam

Çözümleyiciler Visual Studio uzantısı olarak yüklerseniz, çözüm düzeyinde ve Visual Studio 'nun tüm örneklerine uygulanır. Çözümleyicileri, tercih edilen yöntemi olan bir NuGet paketi olarak yüklerseniz, yalnızca NuGet paketinin yüklendiği proje için geçerlidir. Ekip ortamlarında, NuGet paketleri olarak yüklenen çözümleyiciler, o projede çalışan *tüm geliştiriciler* için kapsamdadır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı veya bir sürekli tümleştirme (CI) yapısının parçası olarak, derleme zamanında uygulanan kuralların uygulanmasını sağlamak için, Çözümleyicileri bir NuGet paketi olarak yükler. Çözümleyici uyarıları ve hataları, çözümleyiciler bir uzantı olarak yüklerseniz derleme raporunda gösterilmez.

Aşağıdaki görüntüde, bir çözümleyici kuralı ihlali içeren bir proje derlemeden komut satırı derleme çıkışı gösterilmektedir:

![Kural ihlali ile MSBuild çıkışı](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural önem derecesi

Visual Studio uzantısı olarak yüklenen çözümleyiciler arasından kuralların önem derecesini yapılandıramazsınız. [Kural önem derecesini](../code-quality/use-roslyn-analyzers.md#rule-severity)yapılandırmak için Çözümleyicileri bir NuGet paketi olarak yükler.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri yüklemesi](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler SSS](analyzers-faq.md)
- [Kendi kod çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
