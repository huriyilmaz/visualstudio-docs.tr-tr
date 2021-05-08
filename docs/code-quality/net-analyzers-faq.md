---
title: FxCop kod analizi (ikili analiz) ve .NET çözümleyicileri (kaynak analizi)
ms.date: 09/06/2018
description: Eski FxCop (ikili analiz) ile .NET çözümleyicileri (kaynak analizi) arasındaki farkı Visual Studio. Bu çözümleyicileri kullanmayla ilgili soruların yanıtlarına bakın.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800527"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Eski FxCop ve .NET çözümleyicileri hakkında sık sorulan sorular

Eski FxCop (ikili analiz) ile .NET çözümleyicileri (kaynak analizi) arasındaki farkları anlamak biraz kafa karıştırıcı olabilir. Bu makale, sahip olabileceğiniz bazı soruların yanıtlarını amaçlar.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Eski FxCop ve .NET çözümleyicileri arasındaki fark nedir?

Eski FxCop derleme sonrası analizi derlenmiş bir derlemede çalıştırır. FxCopCmd.exeadlı ayrı bir **yürütülebilir dosya olarak çalışır.** FxCopCmd.exe derlemeyi yükler, kod analizini çalıştırır ve ardından sonuçları (veya *tanılamayı) raporlar.*

.NET çözümleyicileri, .NET Compiler Platform ("Roslyn") temel alır. Bunları [.NET SDK'dan etkinleştirir veya proje ya da](install-net-analyzers.md) çözüm tarafından başvurulan bir NuGet paketi olarak yükleyebilirsiniz. Çözümleyiciler, derleyici yürütmesi sırasında kaynak kodu tabanlı analizler çalıştırabilir. Çözümleyiciler,csc.exe **veyavbc.exe,** derleyici işlemi içinde **barındırıldı** ve proje derlenmişken analiz çalıştırıldı. Çözümleyici sonuçları, derleyici sonuçlarıyla birlikte rapor edilir.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>FxCop çözümleyicileri ile .NET çözümleyicileri arasındaki fark nedir?

FxCop çözümleyicileri ve .NET çözümleyicileri, FxCop CA kurallarının .NET Compiler Platform ("Roslyn") çözümleyicisi uygulamalarını ifade eder. 2019 16.8 Visual Studio .NET 5.0'dan önce, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi olarak gönderildi.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) 2019 Visual Studio 16.8 ve .NET 5.0'dan başlayarak, bu çözümleyiciler [.NET SDK'sı ile birlikte gelir.](/dotnet/fundamentals/code-analysis/overview) NuGet paketi olarak `Microsoft.CodeAnalysis.NetAnalyzers` [da kullanılabilirler.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Lütfen [FxCop çözümleyicileri ' nden .net çözümleyicilerine geçiş](migrate-from-fxcop-analyzers-to-net-analyzers.md)yapmayı düşünün.

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Kod analizini Çalıştır komutu .NET Çözümleyicileri 'ni çalıştırsın mı?

Visual Studio 2019 16,5 sürümünden önce,   >  **çalışma kodu analizini** Çözümle ' yi seçtiğinizde eski analiz yürütülür. Visual Studio 2019 16,5 başlatılıyor, **Kod Analizi Çalıştır** menü seçeneği, seçili proje veya çözüm Için Roslyn tabanlı Çözümleyicileri yürütür. .NET Çözümleyicileri yüklediyseniz, bunlar da yürütülür. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod Için kod analizini El Ile çalıştırma](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis MSBuild proje özelliği çözümleyiciler çalıştıranlar mı?

Hayır. Bir proje dosyasındaki **RunCodeAnalysis** özelliği (örneğin, *. csproj*) yalnızca eski FxCop yürütmek için kullanılır. **FxCopCmd.exe** çağıran bir oluşturma sonrası MSBuild görevi çalıştırır.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Böylece .NET çözümleyiciler nasıl çalıştırılır?

.NET çözümleyiciler çalıştırmak için, önce [bunları .NET SDK 'dan etkinleştirin veya bir NuGet paketi olarak yüklemeniz](install-net-analyzers.md)gerekir. Ardından, Visual Studio 'dan veya MSBuild kullanarak projenizi veya çözümünüzü oluşturun. Roslyn çözümleyicilerinin oluşturabileceği uyarılar ve hatalar **hata listesi** veya komut penceresinde görünür.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>.NET Çözümleyicileri NuGet paketini yükledikten sonra bile uyarı CA0507 alıyorum

.NET Çözümleyicileri yüklemişseniz ancak uyarı almaya devam CA0507 **"" Kod analizini Çalıştır "özelliği, derleme sırasında çalıştırılan FxCop çözümleyicileri 'nin kullanım dışı** bırakılmıştır", [proje dosyanızdaki](../ide/solutions-and-projects-in-visual-studio.md#project-file) **RunCodeAnalysis** MSBuild özelliğini **false** olarak ayarlamanız gerekebilir. Aksi halde, eski analiz her derlemeden sonra yürütülür.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>.NET çözümleyicilerine hangi kurallar eklenmiştir?

.NET çözümleyicilerine eklenen eski analiz kuralları hakkında daha fazla bilgi için bkz. [FxCop kuralı bağlantı noktası durumu](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Kod Analizi uyarıları hata olarak kabul edilir

Projeniz uyarıları hata olarak değerlendirmek için Build seçeneğini kullanıyorsa, çözümleyici uyarıları hata olarak görünebilir. Kod analizi uyarılarının hata olarak kabul önlenmesi için Kod analizi hakkında SSS [bölümüne bakın.](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform çözümleyicilere genel bakış](roslyn-analyzers-overview.md)
- [.NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET çözümleyicilerini yükleme](install-net-analyzers.md)
