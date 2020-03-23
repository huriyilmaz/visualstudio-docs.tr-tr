---
title: Kod çözümlemesi kapatma
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431403"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Yönetilen kod için kaynak kodu çözümlemesi nasıl devre dışı kılır

::: moniker range=">=vs-2019"

Bu sayfa Visual Studio'da kod çözümlemesi devre dışı bırakmanıza yardımcı olur. Devre dışı bırakabileceğiniz şeyin sınırlamaları vardır ve kod çözümlemesi kapatma yordamı birkaç etkene bağlı olarak değişir:

- Proje türü (.NET Çekirdek/Standart ve .NET Çerçevesi)

  .NET Core ve .NET Standard projelerinin Kod Analizi özellikleri sayfasında NuGet paketi olarak yüklenen çözümleyicilerden kod çözümlemesi kapatmanızı sağlayan seçenekler vardır. Daha fazla bilgi için [bkz.](#net-core-and-net-standard-projects) .NET Framework projeleri için kaynak kodu çözümlemesi kapatmak için [bkz.](#net-framework-projects)

- Kaynak analizi ve eski analiz

  Bu konu kaynak kod çözümlemesi için geçerlidir, eski (ikili) çözümleme için değil. Eski çözümlemeyi devre dışı bırakma hakkında bilgi için [bkz: Eski kod çözümlemesini etkinleştirme ve devre dışı bırakma.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

## <a name="net-core-and-net-standard-projects"></a>.NET Çekirdek ve .NET Standart projeleri

Visual Studio 2019 sürüm 16.3'ten başlayarak, Kod Analizi özellikleri sayfasında çözümleyicilerin oluşturma zamanında ve tasarım zamanında çalışıp çalışmadığını kontrol etmeye izin veren iki onay kutusu vardır. Bu seçenekler projeye özgü.

![Visual Studio'da canlı kod analizini etkinleştirme veya devre dışı kılabilir](media/run-on-build-run-live-analysis.png)

Bu sayfayı açmak için **Çözüm Gezgini'ndeki** proje düğümüne sağ tıklayın ve **Özellikler'i**seçin. Kod **Analizi** sekmesini seçin.

- Kaynak çözümlemesi'ni oluşturma zamanında devre dışı kakmak için, **Yapı'da Çalıştır** seçeneğinin işaretlerini kaldırın.
- Canlı kaynak çözümlemesi devre dışı kalmak için **Canlı Çözümleme seçeneğinde Çalıştır'ın** işaretlerini kaldırın.

> [!NOTE]
> Visual Studio 2019 sürüm 16.5'ten başlayarak, isteğe bağlı kod analizi yürütme iş akışını tercih ederseniz, canlı analiz sırasında çözümleyici yürütmeyi devre dışı bırakabilir ve/veya bir proje de veya isteğe bağlı bir çözüm üzerinde kod çözümlemesi oluşturabilir ve el ile tetikleyebilirsiniz. Kod çözümlemesi hakkında daha fazla bilgi için [bkz.](how-to-run-code-analysis-manually-for-managed-code.md)  

## <a name="net-framework-projects"></a>.NET Çerçeve projeleri

Çözümleyiciler için kaynak kodu çözümlemesi kapatmak [için, proje dosyasına](../ide/solutions-and-projects-in-visual-studio.md#project-file)aşağıdaki MSBuild özelliklerinden birini veya birkaçını ekleyin.

| MSBuild özelliği | Açıklama | Varsayılan |
| - | - | - |
| `RunAnalyzersDuringBuild` | Çözümleyicilerin oluşturma zamanında çalışıp çalışmadığını denetler. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Çözümleyicilerin kodu tasarım zamanında canlı olarak analiz edip etmediğini denetler. | `true` |
| `RunAnalyzers` | Hem oluşturma hem de tasarım zamanında çözümleyicileri devre dışı kılabilir. Bu özellik üzerinde `RunAnalyzersDuringBuild` önceliklidir ve `RunAnalyzersDuringLiveAnalysis`. | `true` |

Örnekler:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Kaynak analizi

Visual Studio 2017'de [kaynak çözümlemesi](roslyn-analyzers-overview.md) kapatamazsınız. Çözümleyici hatalarını Hata Listesinden temizlemek istiyorsanız, menü çubuğunda **Analyze** > **Çalıştır Kod Çözümle çözümle ve Etkin Sorunları Bastır'ı** seçerek tüm geçerli ihlalleri bastırabilirsiniz. Daha fazla bilgi için [bkz.](use-roslyn-analyzers.md#suppress-violations)

Visual Studio 2019 sürüm 16.3'ten başlayarak kaynak kodu çözümlemesi'ni kapatabilir veya isteğe bağlı olarak çalıştırabilirsiniz. Visual Studio 2019'a yükseltmeyi düşünün.

## <a name="legacy-analysis"></a>Eski analiz

**Kod Analizi** özellikleri sayfasında eski, yapı zaman çözümlemesi devre dışı kullanabilirsiniz. Daha fazla bilgi için [bkz: Eski kod çözümlemesini etkinleştirin ve devre dışı kılabilir.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [İhlalleri bastırma](use-roslyn-analyzers.md#suppress-violations)
- [Nasıl yapılır: Eski kod çözümlemesini etkinleştirme ve devre dışı](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
