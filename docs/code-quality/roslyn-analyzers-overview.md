---
title: Roslyn analizörlerini kullanarak kod analizi
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
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431286"
---
# <a name="overview-of-source-code-analyzers"></a>Kaynak kod çözümleyicileri genel bakış

.NET Derleyici Platformu ("Roslyn") kod çözümleyicileri C# veya Visual Basic kodunuzu stil, kalite ve sürdürülebilirlik, tasarım ve diğer sorunlar için inceler.

- Bazı analizörler Visual Studio için inşa edilmiştir. Bu çözümleyiciler için tanılama kimliği veya kodu, örneğin IDE0067 biçimi ne dir. Bu yerleşik çözümleyicilerin çoğu [kod stilini](../ide/code-styles-and-code-cleanup.md)inceler ve [metin düzenleyicisi seçenekleri sayfasında](../ide/code-styles-and-code-cleanup.md) veya [EditorConfig dosyasında](../ide/editorconfig-code-style-settings-reference.md)tercihleri yapılandırabilirsiniz. Bir avuç yerleşik çözümleyici kod kalitesine bakar.

- NuGet paketi veya Visual Studio uzantısı olarak ek çözümleyiciler yükleyebilirsiniz. Örnek:

  - [FxCop analizörleri](../code-quality/install-fxcop-analyzers.md), Microsoft'un önerilen kod kalitesi analizörleri
  - [StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator,](https://www.nuget.org/packages/Roslynator.Analyzers/) [XUnit Analizörleri](https://www.nuget.org/packages/xunit.analyzers/)ve [Sonar Analizör](https://www.nuget.org/packages/SonarAnalyzer.CSharp/) gibi üçüncü taraf analizörleri

Kural ihlalleri bir çözümleyici tarafından bulunursa, kod düzenleyicisinde (rahatsız edici kod altında *bir kıvrım* olarak) ve Hata Listesi penceresinde bildirilir.

Birçok çözümleyici kuralı veya *tanılama,* sorunu düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmeleri* vardır. Visual Studio'da yerleşik çözümleyici tanılamanın her birinin ilişkili bir kod düzeltmesi vardır. Kod düzeltmeleri, ampul simgesi menüsünde diğer [Hızlı İşlemtürleri](../ide/quick-actions.md)ile birlikte gösterilir. Bu kod düzeltmeleri hakkında bilgi için [Ortak Hızlı Eylemler'e](../ide/common-quick-actions.md)bakın.

![Çözümleyici ihlali ve Hızlı Eylem kodu düzeltme](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Kaynak kodu analizi ve eski analiz

Roslyn çözümleyicileri tarafından kaynak analizi yönetilen kod için [eski çözümleme](../code-quality/code-analysis-for-managed-code-overview.md) değiştirir. Eski analiz kurallarının çoğu roslyn kod çözümleyicileri olarak yeniden yazılmıştır. .NET Core ve .NET Standard projeleri gibi yeni proje şablonları için eski çözümleme bile mevcut değildir.

Eski çözümleme kuralı ihlalleri gibi, kaynak kodu çözümleme ihlalleri de Visual Studio'daki Hata Listesi penceresinde görünür. Buna ek olarak, kaynak kodu çözümleme ihlalleri de kod düzenleyicisinde rahatsız edici kod altında *kıvrımlar* olarak gösterir. Dalgalı rengi kuralın [önem ayarına](../code-quality/use-roslyn-analyzers.md#rule-severity) bağlıdır. Aşağıdaki resimde,&mdash;biri kırmızı, biri yeşil ve bir gri olmak üzere üç ihlal gösterilmektedir:

![Visual Studio'daki kod düzenleyicisinde squiggles](media/diagnostics-severity-colors.png)

Kod çözümleyicileri, etkinse eski çözümleme gibi, yapı zamanında kodu inceler, ancak siz yazarken de yaşar. Canlı kod çözümlemesi kapsamını yalnızca geçerli belgeyi, tüm açık belgeleri veya çözümün tamamını yürütmek üzere yapılandırabilirsiniz. [Bkz. Nasıl Yapılacağını: Canlı kod çözümlemesi kapsamını yapılandırın.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Kod çözümleyicilerinden gelen oluşturma zamanı hataları ve uyarıları yalnızca çözümleyiciler NuGet paketi olarak yüklenirse gösterilir. Yerleşik çözümleyiciler (örneğin, IDE0067 ve IDE0068) yapı sırasında çalışmaz.

Roslyn kod çözümleyicileri yalnızca eski çözümlemenin yaptığı aynı tür sorunları bildirmekle birlikte, dosyanızdaki veya projenizdeki ihlalin bir veya tüm olaylarını düzeltmenizi kolaylaştırır. Bu *eylemlere kod düzeltmeleri*denir. Kod düzeltmeleri IDE'ye özgü; Visual Studio'da [Hızlı Eylemler](../ide/quick-actions.md)olarak uygulanırlar. Tüm çözümleyici tanılama ilişkili bir kod düzeltmesi vardır.

> [!NOTE]
> Visual Studio 2019 16.5 sürümüöncesinde, **Çözümkodu** > **Analizi** menüsü eski çözümlemesi yürütür. Visual Studio 2019 16.5'i başlatan **Run Code Analysis** menüsü, seçilen proje veya çözüm için Roslyn tabanlı çözümleyicileri yürütür.

Hata Listesindeki kod çözümleyicilerinden gelen ihlalleri ve eski çözümlemesi birbirinden ayırt etmek için **Araç** sütununa bakın. Araç değeri **Çözüm Gezgini'ndeki**çözümleyici derlemelerinden biriyle eşleşiyorsa , örneğin **Microsoft.CodeQuality.Analyzeers**, ihlal bir kod çözümleyicisinden gelir. Aksi takdirde, ihlal eski analiz kaynaklanmaktadır.

![Hata Listesindeki araç sütunu](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Proje dosyasındaki **RunCodeAnalysis** MSBuild özelliği yalnızca eski çözümleme için geçerlidir. Çözümleyiciler yüklerseniz, eski çözümlemenin yapıdan sonra çalışmasını önlemek için **RunCodeAnalysis'i** proje dosyanızda **false** olarak ayarlayın.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketi vsix uzantısı karşı

Roslyn kod analizörleri bir NuGet paketi üzerinden proje başına yüklenebilir. Bazıları Visual Studio uzantısı olarak da mevcuttur, bu durumda Visual Studio'da açtığınız herhangi bir çözüm için geçerlidir. [Çözümleyicileri yüklemek](../code-quality/install-roslyn-analyzers.md)için bu iki yöntem arasında bazı temel davranış farklılıkları vardır.

### <a name="scope"></a>Kapsam

Çözümleyicileri Visual Studio uzantısı olarak yüklerseniz, çözüm düzeyinde ve Visual Studio'nun tüm örneklerine uygulanırlar. Çözümleyicileri tercih edilen yöntem olan NuGet paketi olarak yüklerseniz, bunlar yalnızca NuGet paketinin yüklendiği projeye uygulanır. Ekip ortamlarında, NuGet paketi olarak yüklenen çözümleyiciler, bu proje üzerinde çalışan *tüm geliştiriciler* için kapsamdadır.

### <a name="build-errors"></a>Yapı hataları

Komut satırı aracılığıyla veya sürekli tümleştirme (CI) oluşturmanın bir parçası olarak dahil olmak üzere, oluşturma zamanında uygulanan kuralların olması için çözümleyicileri NuGet paketi olarak yükleyin. Çözümleyici uyarılarını ve hatalarını, çözümleyicileri uzantı olarak yüklerseniz yapı raporunda gösterilmez.

Aşağıdaki resimde, çözümleyici kural ihlali içeren bir proje oluşturma komut satırı yapı çıktısı gösterilmektedir:

![Kural ihlali ile MSBuild çıktısı](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural şiddeti

Visual Studio uzantısı olarak yüklenen çözümleyicilerden kuralların önem derecesini yapılandıramazsınız. [Kural önem derecesini](../code-quality/use-roslyn-analyzers.md#rule-severity)yapılandırmak için çözümleyicileri NuGet paketi olarak yükleyin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio'ya kod çözümleyicileri yükleme](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio'da kod çözümleyicilerini kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler hakkında SSS](analyzers-faq.md)
- [Kendi kod çözümleyicinizi yazın](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK’sı](/dotnet/csharp/roslyn-sdk/)
