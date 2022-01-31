---
title: Kod analizini kapatma
ms.date: 01/20/2022
description: .NET Core, Visual Studio projelerinde kaynak kodu analizini .NET Standard ve .NET Framework öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: fdfa36298af77197d287374929d9d90e66e09e2a
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886481"
---
# <a name="disable-source-code-analysis-for-net"></a>.NET için kaynak kod analizini devre dışı bırakma

::: moniker range=">=vs-2022"

Bu sayfa, kod analizini devre dışı bırakmanıza yardımcı Visual Studio. Devre dışı bırakabilirsiniz ve kod analizini kapatma yordamı birkaç faktöre bağlı olarak farklılık gösterir:

- Project türü (.NET Core/Standard ve .NET Framework)

  .NET Core ve .NET Standard projelerinin Code Analysis paket olarak yüklenmiş çözümleyicilerden kod analizini kapatmasına izin NuGet vardır. Daha fazla bilgi için bkz. [.NET Core ve .NET Standard.](#net-core-and-net-standard-projects) Kaynak kod analizini .NET Framework kapatmak için bkz[. .NET Framework.](#net-framework-projects)

- Kaynak analiziyle eski analiz karşılaştırması

  Bu makale eski (ikili) analiz için değil kaynak kodu analizi için geçerlidir. Eski analizi devre dışı bırakma hakkında bilgi için bkz [. Nasıl 2012: Eski kod analizini etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.NET Core ve .NET Standard projeleri

Visual Studio 2022 sürüm 17.0.4'te başlayarak, Code Analysis özellikleri sayfasında çözümleyicilerin derleme zamanında ve tasarım zamanında çalıştırıp çalışmay olmadığını denetlemeye yönelik iki onay kutusu vardır. Bu seçenekler projeye özgü seçeneklerdir.

![Canlı kod analizini etkinleştirme veya devre dışı bırakma veya Visual Studio](media/run-on-build-run-live-analysis-1.png)

Bu sayfayı açmak için, proje düğümüne sağ tıklayın ve **Çözüm Gezgini'yi** **seçin**. Code Analysis **sekmesini seçin**.

- Derleme zamanında kaynak analizini devre dışı bırakmak için Derlemede **çalıştır seçeneğinin işaretini** kaldırın.
- Canlı kaynak analizini devre dışı bırakmak için Canlı **analizde çalıştır seçeneğinin işaretini** kaldırın.

> [!NOTE]
> 2022 Visual Studio 17.0.4 sürümünden başlayarak, isteğe bağlı kod analizi yürütme iş akışını tercih ediyorsanız canlı analiz sırasında çözümleyici yürütmeyi devre dışı abilirsiniz. Ya da bir proje veya isteğe bağlı çözüm üzerinde bir kez kod analizini el ile derleme ve tetikleme. Kod analizini el ile çalıştırma hakkında bilgi için bkz[. Nasıl yapılır: Yönetilen Kod Code Analysis El ile Çalıştırma](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework projeleri

Çözümleyiciler için kaynak kod analizini kapatmak için proje dosyasına aşağıdaki MSBuild veya daha [fazlasını ekleyin](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild özelliği | Description | Varsayılan |
| - | - | - |
| `RunAnalyzersDuringBuild` | Çözümleyicilerin derleme zamanında çalıştırıp çalışmay olmadığını kontrol eder. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Çözümleyicilerin tasarım zamanında kodu canlı olarak analiz edip etmey olmadığını kontrol eder. | `true` |
| `RunAnalyzers` | Hem derleme hem de tasarım zamanında çözümleyicileri devre dışı bırakma. Bu özellik ve 'den önceliklidir `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`. | `true` |

Örnekler:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2019"

Bu sayfa, kod analizini devre dışı bırakmanıza yardımcı Visual Studio. Devre dışı bırakabilirsiniz ve kod analizini kapatma yordamı birkaç faktöre bağlı olarak farklılık gösterir:

- Project türü (.NET Core/Standard ve .NET Framework)

  .NET Core ve .NET Standard projelerinin Code Analysis paket olarak yüklenmiş çözümleyicilerden kod analizini kapatmasına izin NuGet vardır. Daha fazla bilgi için bkz. [.NET Core ve .NET Standard.](#net-core-and-net-standard-projects) Kaynak kod analizini .NET Framework kapatmak için bkz[. .NET Framework.](#net-framework-projects)

- Kaynak analiziyle eski analiz karşılaştırması

  Bu makale eski (ikili) analiz için değil kaynak kodu analizi için geçerlidir. Eski analizi devre dışı bırakma hakkında bilgi için bkz [. Nasıl 2012: Eski kod analizini etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.NET Core ve .NET Standard projeleri

Visual Studio 2019 sürüm 16.3'te başlayarak, Code Analysis özellikleri sayfasında çözümleyicilerin derleme zamanında ve tasarım zamanında çalıştırıp çalışmama konusunda denetime sahip olan iki onay kutusu vardır. Bu seçenekler projeye özgü seçeneklerdir.

![Canlı kod analizini etkinleştirme veya devre dışı bırakma veya Visual Studio](media/run-on-build-run-live-analysis.png)

Bu sayfayı açmak için, proje düğümüne sağ tıklayın ve **Çözüm Gezgini'yi** **seçin**. Code Analysis **sekmesini seçin**.

- Derleme zamanında kaynak analizini devre dışı bırakmak için Derlemede **çalıştır seçeneğinin işaretini** kaldırın.
- Canlı kaynak analizini devre dışı bırakmak için Canlı **analizde çalıştır seçeneğinin işaretini** kaldırın.

> [!NOTE]
> Visual Studio 2019 sürüm 16.5'te başlayarak, isteğe bağlı kod analizi yürütme iş akışını tercih ediyorsanız canlı analiz sırasında çözümleyici yürütmeyi devre dışı ekleyebilirsiniz ya da proje veya isteğe bağlı bir çözümde kod analizini bir kez derleme ve el ile tetikleme. Kod analizini el ile çalıştırma hakkında bilgi için bkz[. Nasıl yapılır: Yönetilen Kod Code Analysis El ile Çalıştırma](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework projeleri

Çözümleyiciler için kaynak kod analizini kapatmak için proje dosyasına aşağıdaki MSBuild veya daha [fazlasını ekleyin](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild özelliği | Description | Varsayılan |
| - | - | - |
| `RunAnalyzersDuringBuild` | Çözümleyicilerin derleme zamanında çalıştırıp çalışmay olmadığını kontrol eder. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Çözümleyicilerin tasarım zamanında kodu canlı olarak analiz edip etmey olmadığını kontrol eder. | `true` |
| `RunAnalyzers` | Hem derleme hem de tasarım zamanında çözümleyicileri devre dışı bırakma. Bu özellik ve 'den önceliklidir `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`. | `true` |

Örnekler:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Kaynak analizi

2017'de [kaynak](roslyn-analyzers-overview.md) analizini Visual Studio kapataaz. Çözümleyici hatalarını Hata Listesinden temizlemek **için Analiz** >  Çalıştır'ı ve menü çubuğunda Etkin Sorunları Code Analysis'yi seçerek tüm geçerli **ihlalleri** bastırabilirsiniz. Daha fazla bilgi için bkz [. İhlalleri gizleme](use-roslyn-analyzers.md#suppress-violations).

2019 Visual Studio 16.3 sürümünden başlayarak kaynak kodu analizini kapatabilir veya isteğe bağlı olarak yürütebilirsiniz. Visual Studio 2019'a yükseltmeyi göz önünde bulundurarak.

## <a name="legacy-analysis"></a>Eski analiz

Eski, derleme zamanı analizini **Code Analysis devre dışı** abilirsiniz. Daha fazla bilgi için, bkz [. How to: Enable and disable legacy code analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [İhlalleri gizleme](use-roslyn-analyzers.md#suppress-violations)
- [Nasıl olur: Eski kod analizini etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
