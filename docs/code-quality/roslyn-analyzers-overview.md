---
title: Roslyn çözümleyicilerini kullanarak kod analizi
ms.date: 09/01/2020
description: Kaynak kod analizi hakkında bilgi sahibi Visual Studio. Kod düzeltmeleri ve farklı çözümleyici türleri ile önem derecesi hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798342"
---
# <a name="overview-of-source-code-analysis"></a>Kaynak kodu analizine genel bakış

.NET Compiler Platform (Roslyn) Çözümleyicileri C# veya stil Visual Basic, bakım, tasarım ve diğer sorunlar için kodlarınızı inceler. Bu inceleme veya analiz, tüm açık dosyalarda tasarım zamanında yapılır.

Çözümleyiciler aşağıdaki gruplara ayrılmalıdır:

- [Kod stili](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) çözümleyiciler, yerleşik olarak Visual Studio. Bu çözümleyiciler için tanılama kimliği veya kod IDExxxx biçimindedir, örneğin, IDE0067. Tercihleri metin düzenleyici seçenekleri [sayfasında veya editorConfig](../ide/code-styles-and-code-cleanup.md) dosyasında [yapılandırabilirsiniz.](/dotnet/fundamentals/code-analysis/code-style-rule-options) .NET 5.0'dan başlayarak, kod stili çözümleyicileri .NET SDK'sı ile birlikte gelir ve derleme uyarıları veya hatalar olarak katı bir şekilde zorlanabilir. Daha fazla bilgi için buraya [bakın.](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis)

- [Kod kalitesi](/dotnet/fundamentals/code-analysis/quality-rules/index) çözümleyicileri artık .NET 5 SDK'sı ile birlikte gelir ve varsayılan olarak etkindir. Bu çözümleyiciler için tanılama kimliği veya kod CAxxxx biçimindedir, örneğin CA1822. Daha fazla bilgi için [bkz. .NET kod kalitesi analizine genel bakış.](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)

- Üçüncü taraf çözümleyiciler bir NuGet paketi veya bir Visual Studio yükleyebilir. [StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)ve Sonar Analyzer gibi üçüncü [taraf çözümleyicileri.](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="severity-levels-of-analyzers"></a>Çözümleyicilerin önem derecesi

Her çözümleyici aşağıdaki önem düzeylerinden birini içerir:

| Önem Derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *hata* olarak görünür ve yapıların başarısız olmasına neden olur.| Sorunlu kodun kırmızı renkli bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *Uyarı* olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Sorunlu kodun yeşil bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıktısında değil, Hata Listesi *iletiler* olarak görünür. | Sorunlu kodun gri dalgalı çizgi ile altı çizilir ve kaydırma çubuğundaki küçük bir gri kutusuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Yok | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

![Hata Listesi penceresinde çözümleyici ihlali](../code-quality/media/code-analysis-error-list.png)

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri, kod düzenleyicisinde rahatsız eden kodun altında geçişler olarak da gösterilir. Aşağıdaki görüntüde bir hata (kırmızı geçiş), bir uyarı (yeşil geçiş) ve bir öneri (üç gri nokta) olmak için üç &mdash; ihlal gösterilir:

![Visual Studio'de kod düzenleyicisinde Visual Studio](media/diagnostics-severity-colors.png)

Birçok çözümleyici kuralı *veya tanılama,* kural ihlallerini düzeltmek için uygulayabilecek *bir veya* daha fazla ilişkili kod düzeltmesi içerir. Kod düzeltmeleri, diğer Hızlı Eylemler türleriyle birlikte ampul simgesi menüsünde [gösterilir.](../ide/quick-actions.md) Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Yaygın Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve Hızlı Eylem kod düzeltmesi](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Çözümleyici önem derecelerini yapılandırma

Çözümleyici kurallarının önem derecelerini veya *tanılamayı* bir [EditorConfig dosyasında veya](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) ampul [menüsünden yapılandırabilirsiniz.](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)

Çözümleyiciler, siz yazarak derleme zamanında kodu inceler ve canlı olarak da yalıtabilir. Canlı kod analizinin kapsamını yalnızca geçerli belge, tüm açık belgeler veya çözümün tamamı için yürütecek şekilde yapılandırabilirsiniz. Bkz. [Nasıl yapılandırılır: Canlı kod analizinin kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Kod çözümleyicilerinden gelen derleme zamanı hataları ve uyarıları yalnızca çözümleyiciler bir NuGet paketi olarak yüklüyse gösterilir. Yerleşik çözümleyiciler (örneğin, IDE0067 ve IDE0068) derleme sırasında hiçbir zaman çalışmaz.

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketiyle VSIX uzantısı karşılaştırması

Üçüncü taraf çözümleyicileri bir NuGet paketi aracılığıyla proje başına yükleyebilir. Bazıları, bir Visual Studio uzantısı olarak da kullanılabilir. Bu durumda, bu uzantılar Visual Studio. Çözümleyicileri yüklemenin bu iki yöntemi arasında bazı önemli [davranış farklılıkları vardır.](../code-quality/install-roslyn-analyzers.md)

### <a name="scope"></a>Kapsam

Çözümleyicileri bir çözümleyici Visual Studio olarak yüklüler, çözüm düzeyinde ve tüm örneklerde Visual Studio. Çözümleyicileri tercih edilen yöntem olan bir NuGet paketi olarak yüklürsanız, bunlar yalnızca NuGet paketinin yük olduğu projeye uygulanır. Ekip ortamlarında, NuGet paketleri olarak yüklenen çözümleyiciler, o projede çalışan *tüm geliştiriciler* için kapsamdadır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı ya da bir sürekli tümleştirme (CI) yapısının parçası olarak, derleme zamanında uygulanmasını sağlamak için aşağıdaki seçeneklerden birini seçebilirsiniz:

- .NET SDK 'da varsayılan olarak çözümleyiciler içeren bir .NET 5,0 projesi oluşturun. Kod analizi, .NET 5.0 veya sonraki sürümleri hedefleyen projeler için varsayılan olarak etkindir. [Enablenetçözümleyiciler](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) özelliğini true olarak ayarlayarak, önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz.

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

- [Çözümleyiciler hakkında SSS](analyzers-faq.yml)
- [Kendi kod çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK’sı](/dotnet/csharp/roslyn-sdk/)