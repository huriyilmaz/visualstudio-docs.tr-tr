---
title: Roslyn çözümleyicilerini kullanarak kod analizi
ms.date: 09/01/2020
description: Kaynak kodu analizi hakkında bilgi sahibi Visual Studio. Kod düzeltmeleri ve farklı çözümleyici türleri ile önem derecesi hakkında bilgi edinmek.
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
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: a0b477f4dcb5d7c2148b40f648c41b9fea5a1578
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631844"
---
# <a name="overview-of-source-code-analysis"></a>Kaynak kodu analizine genel bakış

.NET Compiler Platform (Roslyn) Çözümleyicileri C# veya stil Visual Basic kalite, bakım, tasarım ve diğer sorunlar için kodlarınızı inceler. Bu inceleme veya analiz, tüm açık dosyalarda tasarım zamanında yapılır.

Çözümleyiciler aşağıdaki gruplara ayrılmalıdır:

- [Kod stili](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) çözümleyiciler, yerleşik olarak Visual Studio. Bu çözümleyicilerin tanılama kimliği veya kodu IDExxxx biçimindedir, örneğin, IDE0067. Tercihleri metin düzenleyici seçenekleri [sayfasında veya editorConfig](../ide/code-styles-and-code-cleanup.md) dosyasında [yapılandırabilirsiniz.](/dotnet/fundamentals/code-analysis/code-style-rule-options) .NET 5.0'dan başlayarak, kod stili çözümleyiciler .NET SDK'sı ile birlikte gelir ve derleme uyarıları veya hatalar olarak katı bir şekilde zorlanabilir. Daha fazla bilgi için buraya [bakın.](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis)

- [Kod kalitesi](/dotnet/fundamentals/code-analysis/quality-rules/index) çözümleyicileri artık .NET 5 SDK'sı ile birlikte gelir ve varsayılan olarak etkinleştirilir. Bu çözümleyiciler için tanılama kimliği veya kod CAxxxx biçimindedir, örneğin CA1822. Daha fazla bilgi için [bkz. .NET kod kalitesi analizine genel bakış.](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)

- Üçüncü taraf çözümleyiciler bir NuGet paketi veya Visual Studio yükleyebilir. [StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)ve Sonar Analyzer gibi üçüncü [taraf çözümleyiciler.](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="severity-levels-of-analyzers"></a>Çözümleyicilerin önem derecesi

Her çözümleyici aşağıdaki önem düzeylerinden birini içerir:

| Önem Derecesi (Çözüm Gezgini) | Önem Derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Hatalar olarak görünür ve derlemelerin başarısız olmasına neden olur.| Rahatsız olan kodun altı kırmızı bir çizgiyle çizili ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenmiştir. |
| Uyarı | `warning` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Uyarılar olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Soruna neden olan kodun altı yeşil bir geçişle çizili ve kaydırma çubuğunda küçük bir yeşil kutuyla işaretlenmiştir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıkışında değil Hata Listesinde İletiler olarak görünür.  | Soruna neden olan kod, gri bir geçişle altı çizili ve kaydırma çubuğunda küçük bir gri kutuyla işaretlenmiştir. |
| Gizli | `silent` | Kullanıcı tarafından görülemeyebilir. | Kullanıcı tarafından görülemeyebilir. Ancak tanılama, IDE tanılama altyapısına raporlandı. |
| Hiçbiri | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelen. Bir kuralın varsayılan değerini belirlemek için aşağıdaki Özellikler penceresi. | Kuralın varsayılan önem derecesine karşılık gelen. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (soruna neden olan kodun altında bir geçiş olarak) ve Hata Listesi penceresinde rapor edilir. 

![Hata Listesi penceresinde çözümleyici ihlali](../code-quality/media/code-analysis-error-list.png)

Hata listesinde bildirilen çözümleyici ihlalleri, [kuralın önem derecesi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eş görünür. Çözümleyici ihlalleri, kod düzenleyicisinde rahatsız eden kodun altında geçişler olarak da gösterilir. Aşağıdaki görüntüde bir hata (kırmızı geçiş), bir uyarı (yeşil geçiş) ve bir öneri (üç gri nokta) olmak için üç &mdash; ihlal gösterilir:

![Visual Studio'da kod düzenleyicisinde Visual Studio](media/diagnostics-severity-colors.png)

Birçok çözümleyici kuralı veya *tanılama,* kural ihlallerini düzeltmek için uygulayabilecek *bir* veya daha fazla ilişkili kod düzeltmesi içerir. Kod düzeltmeleri, diğer Hızlı Eylemler türleriyle birlikte ampul simgesi menüsünde [gösterilir.](../ide/quick-actions.md) Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Yaygın Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve Hızlı Eylem kod düzeltmesi](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Çözümleyici önem derecelerini yapılandırma

Çözümleyici kurallarının önem derecelerini veya *tanılamayı* bir [EditorConfig dosyasında veya](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) ampul [menüsünden yapılandırabilirsiniz.](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)

Çözümleyiciler, siz yazarak derleme zamanında kodu inceler ve canlı olarak da yalıtabilir. Canlı kod analizinin kapsamını yalnızca geçerli belge, tüm açık belgeler veya çözümün tamamı için yürütecek şekilde yapılandırabilirsiniz. Bkz. [Nasıl yapılandırılır: Canlı kod analizinin kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Kod çözümleyicilerinden gelen derleme zamanı hataları ve uyarıları yalnızca çözümleyiciler bir derleme paketi olarak NuGet gösterilir. Yerleşik çözümleyiciler (örneğin, IDE0067 ve IDE0068) derleme sırasında hiçbir zaman çalışmaz.

## <a name="nuget-package-versus-vsix-extension"></a>NuGet VSIX uzantısına karşı

Üçüncü taraf çözümleyiciler, proje başına bir NuGet yükleyebilir. Bunların bazıları, Visual Studio uzantısı olarak da kullanılabilir. Bu durumda bunlar, Visual Studio. Çözümleyicileri yüklemenin bu iki yöntemi arasında bazı önemli [davranış farklılıkları vardır.](../code-quality/install-roslyn-analyzers.md)

### <a name="scope"></a>Kapsam

Çözümleyicileri bir Visual Studio uzantısı olarak yüklüler, çözüm düzeyinde ve tüm çözüm örneklerine Visual Studio. Çözümleyicileri tercih edilen yöntem olan NuGet paketi olarak yüklemeniz, yalnızca NuGet paketinin yük olduğu projeye uygulanır. Takım ortamlarında, uygulama paketleri olarak NuGet çözümleyiciler, bu proje üzerinde *çalışmakta olan* tüm geliştiricilerin kapsamındadır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı aracılığıyla veya sürekli tümleştirme (CI) derlemesi kapsamında dahil olmak üzere derleme zamanında kuralların uygulanması için aşağıdaki seçeneklerden birini seçebilirsiniz:

- .NET SDK'da varsayılan olarak çözümleyicileri içeren bir .NET 5.0 projesi oluşturun. Kod analizi, .NET 5.0 veya sonraki sürümleri hedefleyen projeler için varsayılan olarak etkindir. [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) özelliğini true olarak ayarerek önceki .NET sürümlerini hedef alan projelerde kod analizini etkinleştirebilirsiniz.

- Çözümleyicileri bir NuGet yükleyin. Çözümleyicileri bir uzantı olarak yüklemiş olursanız derleme raporunda çözümleyici uyarıları ve hataları gösternmıyor.

Aşağıdaki görüntüde çözümleyici kuralı ihlali içeren bir proje derlemenin komut satırı derleme çıktısı gösterilir:

![MSBuild ihlali olan bir çıkış](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural önem derecesi

Uygulama uzantısı olarak yüklenmiş çözümleyicilerden kuralların önem derecelerini Visual Studio yapılandıramazsiniz. Kural önem [derecelerini yapılandırmak](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)için çözümleyicileri bir NuGet yükleyin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Kod çözümleyicilerini Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Kod çözümleyicilerini Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyiciler hakkında SSS](analyzers-faq.yml)
- [Kendi kod çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK’sı](/dotnet/csharp/roslyn-sdk/)