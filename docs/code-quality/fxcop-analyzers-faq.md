---
title: FxCop kod analizi ve FxCop analizörleri
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431371"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop ve FxCop analizörleri hakkında sık sorulan sorular

Bu eski FxCop ve FxCop analizörleri arasındaki farkları anlamak için biraz kafa karıştırıcı olabilir. Bu makalede, bazı sorular olabilir ele amaçlamaktadır.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Eski FxCop ve FxCop analizörleri arasındaki fark nedir?

Eski FxCop derlenmiş bir derleme de post-build analizi çalışır. **Bu fxCopCmd.exe**denilen ayrı bir yürütülebilir olarak çalışır. FxCopCmd.exe derlenmiş derleme yükler, kod analizi çalışır ve sonra sonuçları (veya *tanılama)* raporlar.

FxCop analizörleri .NET Derleyici Platformu'na ("Roslyn") dayanmaktadır. Bunları proje veya çözüm tarafından başvurulan [bir NuGet paketi olarak yüklersiniz.](install-fxcop-analyzers.md#nuget-package) FxCop çözümleyicileri derleyici yürütme sırasında kaynak kodu tabanlı analiz çalıştırın. FxCop analizörleri derleyici işlemi içinde barındırılır, **csc.exe** veya **vbc.exe**, ve proje inşa edildiğinde analiz çalıştırın. Çözümleyici sonuçları derleyici sonuçları ile birlikte raporlanır.

> [!NOTE]
> Ayrıca [Bir Visual Studio uzantısı olarak FxCop analizörleryükleyebilirsiniz.](install-fxcop-analyzers.md#vsix) Bu durumda, çözümleyiciler kod düzenleyicisini yazarken çalıştırın, ancak oluşturma zamanında yürütmezler. Sürekli tümleştirmenin (CI) bir parçası olarak FxCop çözümleyicilerini çalıştırmak istiyorsanız, bunları nuget paketi olarak yükleyin.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Run Code Analysis komutu FxCop çözümleyicilerini çalıştırıyor mu?

Visual Studio 2019 16.5 sürümüne kadar, **Çözümle** > **Kodu Çözümle'yi**seçtiğinizde, eski çözümlemesi yürütür. Visual Studio 2019 16.5'i başlatan **Run Code Analysis** menüsü, seçilen proje veya çözüm için Roslyn tabanlı çözümleyicileri yürütür. Roslyn tabanlı FxCop analizörleri yüklediyseniz, bunlar da yürütülür. Daha fazla bilgi için [bkz: Yönetilen Kod için Kod Analizini El Ile Çalıştırın.](how-to-run-code-analysis-manually-for-managed-code.md)

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild proje özelliği çözümleyicileri çalıştırıyor mu?

Hayır. Bir proje dosyasındaki **RunCodeAnalysis** özelliği (örneğin, *.csproj)* yalnızca eski FxCop'u çalıştırmak için kullanılır. **Bu FxCopCmd.exe**çağırır bir post-build msbuild görev çalışır.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Peki nasıl FxCop analizörleri sonra çalıştırın?

FxCop analizörlerini çalıştırmak için önce [nuget paketini yükleyin.](install-fxcop-analyzers.md) Ardından Visual Studio'dan projenizi veya çözümünüzü oluşturun veya msbuild'i kullanarak. FxCop çözümleyicilerinin oluşturduğu uyarılar ve hatalar **Hata Listesi'nde** veya komut penceresinde görünür.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Ben FxCop analizörleri NuGet paketi yükledikten sonra bile uyarı CA0507 olsun

FxCop analizörleri yüklediyseniz ancak ca0507 ""Run Code Analysis" uyarı almaya devam **ederseniz, yapı sırasında çalışan FxCop analizörleri lehine amortismana**uğrama devam etti, [proje dosyanızdaki](../ide/solutions-and-projects-in-visual-studio.md#project-file) **RunCodeAnalysis** msbuild özelliğini **yanlış**olarak ayarlamanız gerekebilir. Aksi takdirde, eski çözümleme her yapıdan sonra yürütülür.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>FxCop analizörlerine hangi kurallar iletilmiştir?

[FxCop analizörlerine](install-fxcop-analyzers.md)hangi eski analiz kurallarının iletildiği hakkında bilgi için [Bkz. Fxcop kural bağlantı noktası durumu.](fxcop-rule-port-status.md)

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Kod analizi uyarıları hata olarak kabul edilir

Projeniz uyarıları hata olarak ele almak için yapı seçeneğini kullanıyorsa, FxCop çözümleyici uyarıları hata olarak görünebilir. Kod çözümleme uyarılarının hata olarak değerlendirilmesini önlemek için, [Kod çözümlemesi SSS'deki](../code-quality/analyzers-faq.md#treat-warnings-as-errors)adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Derleyici Platformu analizörlerinden genel bakış](roslyn-analyzers-overview.md)
- [FxCop analizörlerine geçiş](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [FxCop çözümleyicilerini yükleme](install-fxcop-analyzers.md)
