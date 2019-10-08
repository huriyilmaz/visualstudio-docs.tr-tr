---
title: FxCop kod analizi ve FxCop çözümleyicileri
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 277155bdab713ec12daa380fc2721a31b5d932a2
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000124"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop ve FxCop çözümleyicileri hakkında sık sorulan sorular

Eski FxCop ve FxCop çözümleyicileri arasındaki farkları anlamak biraz kafa karıştırıcı olabilir. Bu makalede, karşılaşabileceğiniz soruların bazılarını ele alabilirsiniz.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Eski FxCop ve FxCop çözümleyicileri arasındaki fark nedir?

Eski FxCop derleme sonrası analizini derlenmiş bir derlemede çalıştırır. **FxCopCmd. exe**adlı ayrı bir yürütülebilir dosya olarak çalışır. FxCopCmd. exe derlenen derlemeyi yükler, Kod analizini çalıştırır ve sonuçları (veya *tanılamayı*) raporlar.

FxCop çözümleyicileri .NET Compiler Platform ("Roslyn") temel alır. Bunları, proje veya çözüm tarafından başvurulan [bir NuGet paketi olarak yüklersiniz](install-fxcop-analyzers.md#nuget-package) . FxCop çözümleyicileri, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırır. FxCop çözümleyicileri, **CSC. exe** veya **Vbc. exe**derleyici işlemi içinde barındırılır ve proje oluşturulduğunda Analizi çalıştırır. Çözümleyici sonuçları derleyici sonuçlarıyla birlikte raporlanır.

> [!NOTE]
> [Visual Studio uzantısı olarak FxCop çözümleyicileri de yükleyebilirsiniz](install-fxcop-analyzers.md#vsix). Bu durumda, çözümleyiciler kod düzenleyicisine yazarken yürütülür, ancak derleme zamanında yürütülmez. FxCop çözümleyicileri 'ni sürekli tümleştirme (CI) kapsamında çalıştırmak istiyorsanız, bunları bir NuGet paketi olarak yükleyebilirsiniz.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Kod analizini Çalıştır komutu FxCop çözümleyicileri çalıştırmalıdır mi?

Hayır. @No__t **analiz**' nı seçtiğinizde,**Kod analizini Çalıştır**' ı seçtiğinizde eski analiz yürütülür. **Çalışma kodu analizinin** , Roslyn tabanlı FxCop çözümleyicileri dahil olmak üzere Roslyn tabanlı çözümleyiciler üzerinde hiçbir etkisi yoktur.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis MSBuild proje özelliği çözümleyiciler çalıştıranlar mı?

Hayır. Bir proje dosyasındaki **RunCodeAnalysis** özelliği (örneğin, *. csproj*) yalnızca eski FxCop yürütmek için kullanılır. **FxCopCmd. exe**' yi çağıran bir oluşturma sonrası MSBuild görevi çalıştırır. Bu, Visual Studio 'da **analiz** > **çalıştırma kodu çözümlemesini** seçme ile eşdeğerdir.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Bu nedenle, FxCop çözümleyicileri nasıl çalıştırılır?

FxCop çözümleyicileri 'ni çalıştırmak için önce bunlar için [NuGet paketini yüklemeniz](install-fxcop-analyzers.md) gerekir. Ardından, Visual Studio 'dan veya MSBuild kullanarak projenizi veya çözümünüzü oluşturun. FxCop çözümleyicileri tarafından oluşturulacak uyarılar ve hatalar **hata listesi** veya komut penceresinde görünür.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>FxCop çözümleyicileri NuGet paketini yükledikten sonra bile uyarı CA0507 alıyorum

FxCop çözümleyicileri yüklemişseniz ancak uyarı almaya devam ederseniz **, "" Kod analizini Çalıştır "özelliği derleme sırasında çalıştırılan FxCop çözümleyicileri yararına kullanım dışı**bırakılmıştır. projenizde **RunCodeAnalysis** MSBuild özelliğini ayarlamanız gerekebilir [ dosya](../ide/solutions-and-projects-in-visual-studio.md#project-file) **yanlış**. Aksi halde, eski analiz her derlemeden sonra yürütülür.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>FxCop çözümleyicileri hangi kuralları kapsayan?

[FxCop](install-fxcop-analyzers.md)analizler 'e hangi eski analiz kurallarının oluşturulduğu hakkında daha fazla bilgi için bkz. [FxCop kuralı bağlantı noktası durumu](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Kod Analizi uyarıları hata olarak kabul edilir

Projeniz uyarıları hata olarak değerlendirmek için Build seçeneğini kullanıyorsa, FxCop Çözümleyicisi uyarıları hata olarak görünebilir. Kod Analizi uyarılarının hata olarak işlenmesine engel olmak için, [kod analizi hakkında SSS bölümündeki](../code-quality/analyzers-faq.md#treat-warnings-as-errors)adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform çözümleyicilerine genel bakış](roslyn-analyzers-overview.md)
- [Çözümleyiciler ile çalışmaya başlama](fxcop-analyzers.yml)
- [FxCop çözümleyicileri 'ni yükler](install-fxcop-analyzers.md)
