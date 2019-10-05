---
title: Kod analizini kapat
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77c189e4a15f2ae4049c45d2c8463079895f5be2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975153"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Yönetilen kod için kaynak kodu analizini devre dışı bırakma

::: moniker range=">=vs-2019"

Bu sayfa, Visual Studio 'da Kod analizini devre dışı bırakmanızı sağlar. Devre dışı bırakabilecekleri sınırlamalar vardır ve Kod analizini kapatma yordamı, birkaç etkene göre farklılık gösterir:

- Proje türü (.NET Core/Standard ve .NET Framework)

  .NET Core ve .NET Standard projelerinin kod analizi özellikleri sayfasında, bir NuGet paketi olarak yüklenen çözümleyiciler arasından Kod analizini kapatmanızı sağlayan seçenekler vardır. Daha fazla bilgi için bkz. [.NET Core ve .NET Standard projeleri](#net-core-and-net-standard-projects). .NET Framework projeler için kaynak kodu analizini devre dışı bırakmak için, bkz. [.NET Framework projeler](#net-framework-projects).

- NuGet çözümleyici paketi ve VSıX veya yerleşik çözümleyiciler

  Şu anda, yerleşik çözümleyiciler için Canlı Kod analizini devre dışı bırakamezsiniz, örneğin, kural KIMLIĞI IDE0067. Benzer şekilde, Visual Studio uzantısının (VSıX) bir parçası olarak yüklenen çözümleyiciler için Canlı Kod analizini devre dışı bırakabilirsiniz. Yerleşik ve VSıX tabanlı çözümleyicilerin hatalarını ve uyarılarını gizlemek için **, @no__t-** 1 oluştur ' u seçin ve menü çubuğunda**etkin sorunları gizleyin** . NuGet paketinin bir parçası olarak yüklenen çözümleyiciler için canlı ve yerleşik *Analizi devre dışı bırakabilirsiniz.*

- Kaynak Analizi ve eski analizler

  Bu konu, eski (ikili) analizine değil kaynak kodu analizine yöneliktir. Eski Analizi devre dışı bırakma hakkında daha fazla bilgi için bkz. [Nasıl yapılır: Eski Kod analizini etkinleştirin ve devre dışı bırakın @ no__t-0.

## <a name="net-core-and-net-standard-projects"></a>.NET Core ve .NET Standard projeleri

Visual Studio 2019 sürüm 16,3 ' den başlayarak, kod analizi özellikleri sayfasında, NuGet tabanlı çözümleyiciler oluşturma zamanında ve tasarım zamanında çalışıp çalışmadığını denetlemenize olanak tanıyan iki onay kutusu bulunur. Bu seçenekler projeye özgüdür.

![Visual Studio 'da Canlı Kod analizini veya derlemeyi etkinleştirme veya devre dışı bırakma](media/run-on-build-run-live-analysis.png)

Bu sayfayı açmak için **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **Özellikler**' i seçin. **Kod Analizi** sekmesini seçin.

- Derleme zamanında kaynak analizini devre dışı bırakmak için, **derlemede Çalıştır** seçeneğinin işaretini kaldırın.
- Canlı kaynak analizini devre dışı bırakmak için **canlı olarak çalıştır analiz** seçeneğinin işaretini kaldırın.

> [!NOTE]
> Yerleşik ve VSıX tabanlı çözümleyiciler, **canlı Analize Çalıştır** işaretli olsa bile kodunuzun canlı analizini sağlamaya devam edecektir. Bu çözümleyiciler içindeki hataları ve uyarıları gizlemek istiyorsanız **, @no__t-** 1 oluştur ' u seçin ve menü çubuğunda**etkin sorunları gizleyin** .

## <a name="net-framework-projects"></a>.NET Framework projeleri

NuGet paketinin bir parçası olarak yüklenen çözümleyiciler için kaynak kodu analizini devre dışı bırakmak için, aşağıdaki MSBuild özelliklerinden birini veya daha fazlasını [proje dosyasına](../ide/solutions-and-projects-in-visual-studio.md#project-file)ekleyin.

| MSBuild özelliği | Açıklama | Varsayılan |
| - | - | - |
| `RunAnalyzersDuringBuild` | NuGet tabanlı çözümleyicilerin derleme zamanında çalışıp çalışmadığını denetler. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | NuGet tabanlı çözümleyiciler, kodu tasarım zamanında canlı olarak analiz edip etmediğini denetler. | `true` |
| `RunAnalyzers` | Hem derleme hem de tasarım zamanında NuGet tabanlı Çözümleyicileri devre dışı bırakır. Bu özellik `RunAnalyzersDuringBuild` ve `RunAnalyzersDuringLiveAnalysis` ' den önceliklidir. | `true` |

Örnekler:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Kaynak Analizi

Visual Studio 2017 ' de [kaynak analizini](roslyn-analyzers-overview.md) devre dışı bırakabilirsiniz. Hata Listesi çözümleyici hatalarını gidermek istiyorsanız, **çözümle** > **Kod analizini Çalıştır ve menü çubuğunda etkin sorunları Gizle** seçeneklerini belirleyerek tüm geçerli ihlallerin görüntülenmesini sağlayabilirsiniz. Daha fazla bilgi için bkz. [Ihlalleri gösterme](use-roslyn-analyzers.md#suppress-violations).

Visual Studio 2019 sürüm 16,3 ' den başlayarak NuGet tabanlı kaynak kodu analizini devre dışı bırakabilirsiniz. Visual Studio 2019 ' e yükseltmeyi düşünün.

## <a name="legacy-analysis"></a>Eski analiz

**Kod Analizi** özellikleri sayfasında eski, derleme zamanı analizini devre dışı bırakabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Eski Kod analizini etkinleştirin ve devre dışı bırakın @ no__t-0.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [İhlalleri gösterme](use-roslyn-analyzers.md#suppress-violations)
- [Nasıl yapılır: Eski Kod analizini etkinleştirme ve devre dışı bırakma @ no__t-0
