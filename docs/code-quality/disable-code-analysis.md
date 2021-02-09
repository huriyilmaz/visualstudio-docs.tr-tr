---
title: Kod analizini kapat
ms.date: 09/01/2020
description: .NET Core, .NET Standard ve .NET Framework projelerinde Visual Studio kaynak kodu analizini devre dışı bırakma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 6a1f1466caa921d46ce4701f5074b98f3d5ba051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860392"
---
# <a name="disable-source-code-analysis-for-net"></a>.NET için kaynak kodu analizini devre dışı bırak

::: moniker range=">=vs-2019"

Bu sayfa, Visual Studio 'da Kod analizini devre dışı bırakmanızı sağlar. Devre dışı bırakabilecekleri sınırlamalar vardır ve Kod analizini kapatma yordamı, birkaç etkene göre farklılık gösterir:

- Proje türü (.NET Core/Standard ve .NET Framework)

  .NET Core ve .NET Standard projelerinin kod analizi özellikleri sayfasında, bir NuGet paketi olarak yüklenen çözümleyiciler arasından Kod analizini kapatmanızı sağlayan seçenekler vardır. Daha fazla bilgi için bkz. [.NET Core ve .NET Standard projeleri](#net-core-and-net-standard-projects). .NET Framework projeler için kaynak kodu analizini devre dışı bırakmak için, bkz. [.NET Framework projeler](#net-framework-projects).

- Kaynak Analizi ve eski analizler

  Bu konu, eski (ikili) analizine değil kaynak kodu analizine yöneliktir. Eski Analizi devre dışı bırakma hakkında bilgi için bkz. [nasıl yapılır: etkinleştirme ve devre dışı bırakma eski kod analizi](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.NET Core ve .NET Standard projeleri

Visual Studio 2019 sürüm 16,3 ' den başlayarak, kod analizi özellikleri sayfasında analizler 'in derleme zamanında ve tasarım zamanında çalışıp çalışmadığını denetlemenize olanak tanıyan iki onay kutusu bulunur. Bu seçenekler projeye özgüdür.

![Visual Studio 'da Canlı Kod analizini veya derlemeyi etkinleştirme veya devre dışı bırakma](media/run-on-build-run-live-analysis.png)

Bu sayfayı açmak için **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **Özellikler**' i seçin. **Kod Analizi** sekmesini seçin.

- Derleme zamanında kaynak analizini devre dışı bırakmak için, **derlemede Çalıştır** seçeneğinin işaretini kaldırın.
- Canlı kaynak analizini devre dışı bırakmak için **canlı olarak çalıştır analiz** seçeneğinin işaretini kaldırın.

> [!NOTE]
> Visual Studio 2019 sürüm 16,5 ' den başlayarak, isteğe bağlı kod analizi yürütme iş akışını tercih ediyorsanız, canlı analiz sırasında çözümleyici yürütmeyi devre dışı bırakabilir ve/veya bir proje ya da istek üzerine bir çözüm oluşturup el ile kod analizi tetikleyebilir. Kod analizini el ile çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod Için kod analizini El Ile çalıştırma](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework projeleri

Çözümleyiciler için kaynak kodu analizini devre dışı bırakmak için, aşağıdaki MSBuild özelliklerinden birini veya daha fazlasını [proje dosyasına](../ide/solutions-and-projects-in-visual-studio.md#project-file)ekleyin.

| MSBuild özelliği | Description | Varsayılan |
| - | - | - |
| `RunAnalyzersDuringBuild` | Çözümleyicilerin derleme zamanında çalıştırılıp çalıştırılmayacağını denetler. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Çözümleyiciler, tasarım zamanında kodu canlı olarak analiz edip etmediğini denetler. | `true` |
| `RunAnalyzers` | Hem derleme hem de tasarım zamanında Çözümleyicileri devre dışı bırakır. Bu özellik `RunAnalyzersDuringBuild` , ve ' den önceliklidir `RunAnalyzersDuringLiveAnalysis` . | `true` |

Örnekler:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Kaynak analizi

Visual Studio 2017 ' de [kaynak analizini](roslyn-analyzers-overview.md) devre dışı bırakabilirsiniz. **Hata listesi** çözümleyici hatalarını temizlemek istiyorsanız, tüm geçerli ihlallerin   >  **Kod analizini çözümle ve menü çubuğunda etkin sorunları Gizle** ' yi seçerek gizleyebilirsiniz. Daha fazla bilgi için bkz. [Ihlalleri gösterme](use-roslyn-analyzers.md#suppress-violations).

Visual Studio 2019 sürüm 16,3 ' den başlayarak, kaynak kodu analizini kapatabilir veya isteğe bağlı olarak yürütebilirsiniz. Visual Studio 2019 ' e yükseltmeyi düşünün.

## <a name="legacy-analysis"></a>Eski analiz

**Kod Analizi** özellikleri sayfasında eski, derleme zamanı analizini devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Eski Kod analizini etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [İhlalleri gösterme](use-roslyn-analyzers.md#suppress-violations)
- [Nasıl yapılır: Eski Kod analizini etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
