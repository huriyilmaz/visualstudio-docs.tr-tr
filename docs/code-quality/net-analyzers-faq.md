---
title: FxCop kod analizi (ikili analiz) ve .NET Çözümleyicileri (kaynak analizi)
ms.date: 09/06/2018
description: Visual Studio 'da eski FxCop (ikili analiz) ve .NET Çözümleyicileri (kaynak analizi) arasındaki farkı anlayın. Bu Çözümleyicileri nasıl kullanacağınızı öğrenmek için bkz. sorulara yanıtlar.
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
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867769"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Eski FxCop ve .NET Çözümleyicileri hakkında sık sorulan sorular

Eski FxCop (ikili analiz) ve .NET Çözümleyicileri (kaynak analizi) arasındaki farkları anlamak biraz kafa karıştırıcı olabilir. Bu makalede, karşılaşabileceğiniz soruların bazılarını ele alabilirsiniz.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Eski FxCop ve .NET Çözümleyicileri arasındaki fark nedir?

Eski FxCop derleme sonrası analizini derlenmiş bir derlemede çalıştırır. **FxCopCmd.exe** olarak adlandırılan ayrı bir yürütülebilir dosya olarak çalışır. FxCopCmd.exe derlenen derlemeyi yükler, Kod analizini çalıştırır ve sonuçları (veya *tanılamayı*) raporlar.

.NET Çözümleyicileri .NET Compiler Platform ("Roslyn") temel alır. [Bunları .NET SDK 'dan etkinleştirebilir veya](install-net-analyzers.md) proje ya da çözüm tarafından başvurulan bir NuGet paketi olarak yükleyebilirsiniz. Çözümleyiciler, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırır. Çözümleyiciler derleyici işlemi içinde barındırılır, **csc.exe** veya **vbc.exe** ve proje oluşturulduğunda Analizi çalıştırır. Çözümleyici sonuçları derleyici sonuçlarıyla birlikte raporlanır.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>FxCop çözümleyicileri ve .NET Çözümleyicileri arasındaki fark nedir?

Hem FxCop çözümleyicileri hem de .NET Çözümleyicileri, FxCop CA kurallarının .NET Compiler Platform ("Roslyn") çözümleyici uygulamalarına başvurur. Visual Studio 2019 16,8 ve .NET 5,0 öncesinde, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)olarak gönderilir. Visual Studio 2019 16,8 ve .NET 5,0 'den başlayarak, bu çözümleyiciler [.NET SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). Bunlar ayrıca `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)olarak da kullanılabilir. Lütfen [FxCop çözümleyicileri ' nden .net çözümleyicilerine geçiş](migrate-from-fxcop-analyzers-to-net-analyzers.md)yapmayı düşünün.

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

Projeniz uyarıları hata olarak değerlendirmek için Build seçeneğini kullanıyorsa, çözümleyici uyarıları hata olarak görünebilir. Kod Analizi uyarılarının hata olarak işlenmesine engel olmak için, [kod analizi hakkında SSS bölümündeki](../code-quality/analyzers-faq.md#treat-warnings-as-errors)adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform çözümleyicilerine genel bakış](roslyn-analyzers-overview.md)
- [.NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET çözümleyicilerini yükleme](install-net-analyzers.md)
