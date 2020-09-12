---
title: Roslyn Çözümleyicileri kullanarak kod analizi
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d61ebaa191e94439629d7ac5f85a6921163ed08b
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036606"
---
# <a name="overview-of-source-code-analysis"></a>Kaynak kodu analizine genel bakış

.NET Compiler Platform (Roslyn) çözümleyiciler stil, kalite, bakım, tasarım ve diğer sorunlar için C# veya Visual Basic kodunuzu inceler. Bu denetleme veya analiz, tüm açık dosyalardaki tasarım zamanı sırasında yapılır. 

Çözümleyiciler aşağıdaki gruplara ayrılabilir:

- [Kod stili](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019#convention-categories) Çözümleyicileri, Visual Studio 'da yerleşik olarak bulunur. Bu çözümleyiciler için tanılama KIMLIĞI veya kodu ıdexxxx biçimindedir, örneğin, IDE0067. Tercihleri, [metin düzenleyici seçenekleri sayfasında](../ide/code-styles-and-code-cleanup.md) veya bir [editorconfig dosyasında](../ide/editorconfig-code-style-settings-reference.md)yapılandırabilirsiniz. .NET 5,0 ' den başlayarak [kod stili](https://docs.microsoft.com/dotnet/fundamentals/productivity/code-analysis) Çözümleyicileri .NET SDK 'ya dahildir.

- [Kod kalitesi](/code-analysis-warnings-for-managed-code-by-checkid.md) Çözümleyicileri artık .NET 5 SDK 'ya dahildir ve varsayılan olarak etkindir. Bu çözümleyiciler için tanılama KIMLIĞI veya kodu CAxxxx biçimindedir, örneğin, CA1822. Daha fazla bilgi için bkz. [.net kaynak kodu analizine genel bakış](/dotnet/fundamentals/productivity/code-analysis).

- Üçüncü taraf Çözümleyicileri, bir NuGet paketi veya bir Visual Studio uzantısı olarak yüklenebilir. [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit Çözümleyicileri](https://www.nuget.org/packages/xunit.analyzers/)ve [sonar Çözümleyicisi](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)gibi üçüncü taraf Çözümleyicileri.

## <a name="severity-levels-of-analyzers"></a>Çözümleyiciler önem düzeyleri

Her çözümleyici aşağıdaki önem düzeylerinden birine sahiptir:

| Önem derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *hata* olarak görünür ve yapıların başarısız olmasına neden olur.| Sorunlu kodun kırmızı renkli bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *Uyarı* olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Sorunlu kodun yeşil bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıktısında değil, Hata Listesi *iletiler* olarak görünür. | Sorunlu kodun gri dalgalı çizgi ile altı çizilir ve kaydırma çubuğundaki küçük bir gri kutusuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Yok | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

![Hata Listesi penceresinde çözümleyici ihlali](../code-quality/media/code-analysis-error-list.png)

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri Ayrıca kod düzenleyicisinde, sorunlu kodun altında dalgalı çizgiler olarak görünür. Aşağıdaki görüntüde &mdash; bir hata (kırmızı dalgalı çizgi), bir uyarı (yeşil dalgalı çizgi) ve bir öneri (üç gri noktalı) olmak üzere üç ihlal gösterilmektedir:

![Visual Studio 'da kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Birçok çözümleyici kuralı veya *tanılaması*, kural ihlalini düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Çözümleyici önem düzeylerini yapılandırma

Çözümleyici kurallarının önem derecesini veya *tanılamayı*bir [editorconfig dosyasında](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) ya da ampul [menüsünden](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)yapılandırabilirsiniz. 

Çözümleyiciler, derleme zamanında kodu incelemek ve siz yazarken canlı olarak yapılandırmak için de yapılandırılabilir. Canlı kod analizinin kapsamını yalnızca geçerli belge, tüm açık belgeler veya tüm çözüm için yürütülecek şekilde yapılandırabilirsiniz. Bkz. [nasıl yapılır: canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Kod Çözümleyicileri içindeki derleme zamanı hataları ve uyarıları yalnızca çözümleyiciler bir NuGet paketi olarak yüklenirse gösterilir. Yerleşik çözümleyiciler (örneğin, IDE0067 ve IDE0068) derleme sırasında hiçbir şekilde çalıştırılmadı.

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketi ve VSıX uzantısı

Üçüncü taraf Çözümleyicileri, bir NuGet paketi aracılığıyla proje başına yüklenebilir. Bazıları Visual Studio uzantısı olarak da kullanılabilir, bu durumda Visual Studio 'da açtığınız tüm çözümler için geçerlidir. Bu iki çözümleyici [yükleme](../code-quality/install-roslyn-analyzers.md)yöntemi arasında bazı önemli davranış farklılıkları vardır.

### <a name="scope"></a>Kapsam

Çözümleyiciler Visual Studio uzantısı olarak yüklerseniz, çözüm düzeyinde ve Visual Studio 'nun tüm örneklerine uygulanır. Çözümleyicileri, tercih edilen yöntemi olan bir NuGet paketi olarak yüklerseniz, yalnızca NuGet paketinin yüklendiği proje için geçerlidir. Ekip ortamlarında, NuGet paketleri olarak yüklenen çözümleyiciler, o projede çalışan *tüm geliştiriciler* için kapsamdadır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı ya da bir sürekli tümleştirme (CI) yapısının parçası olarak, derleme zamanında uygulanmasını sağlamak için aşağıdaki seçeneklerden birini seçebilirsiniz:

- .NET SDK 'da varsayılan olarak çözümleyiciler içeren bir .NET 5,0 projesi oluşturun. Kod Analizi, .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkindir. [Enablenetçözümleyiciler](https://docs.microsoft.com/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) özelliğini true olarak ayarlayarak, önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz.

- Çözümleyicileri bir NuGet paketi olarak yükler. Çözümleyici uyarıları ve hataları, çözümleyiciler bir uzantı olarak yüklerseniz derleme raporunda gösterilmez.

Aşağıdaki görüntüde, bir çözümleyici kuralı ihlali içeren bir proje derlemeden komut satırı derleme çıkışı gösterilmektedir:

![Kural ihlali ile MSBuild çıkışı](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural önem derecesi

Visual Studio uzantısı olarak yüklenen çözümleyiciler arasından kuralların önem derecesini yapılandıramazsınız. [Kural önem derecesini](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)yapılandırmak için Çözümleyicileri bir NuGet paketi olarak yükler.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri yüklemesi](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler hakkında SSS](analyzers-faq.md)
- [Kendi kod çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK’sı](/dotnet/csharp/roslyn-sdk/)
