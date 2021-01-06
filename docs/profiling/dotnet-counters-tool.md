---
title: DotNet sayaçlarını görselleştirin | Microsoft Docs
description: Visual Studio performans profil oluşturucusu 'nda .NET sayaçları aracını kullanmayı öğrenin.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905042"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visual Studio Profiler 'dan DotNet sayaçlarını görselleştirin


.NET sayaçları Aracı, Visual Studio Profiler 'ın içinden zaman içinde [DotNet sayaçlarını](/dotnet/core/diagnostics/dotnet-counters) görselleştirmenize olanak tanır.


> [!NOTE]
> .NET sayaçları Aracı, Visual Studio 2019 sürüm 16,7 veya üzerini gerektirir ve .NET Core 3.0 + ' u hedefler.

## <a name="setup"></a>Kurulum

1. Performans profil oluşturucuyu (**alt + f2** veya **Debug-> Performance Profiler**) Visual Studio 'da açın.

2. **.Net sayaçları** onay kutusunu seçin.

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Sayaçlar aracı seçildi.":::

3. Aracı çalıştırmak için **Başlat** düğmesine tıklayın.

Araç performansını en iyi duruma getirme hakkında daha fazla bilgi için bkz. [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Verilerinizi anlayın

Araç başlangıçta veri toplarken, [DotNet sayaçlarının](/dotnet/core/diagnostics/dotnet-counters)canlı değerlerini görebilirsiniz.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET sayaç aracı toplanıyor.":::

Ayrıca sayaç adlarının yanındaki onay kutusunu seçerek sayaçlara ait grafikleri görüntüleyebilirsiniz. Tek seferde birden çok sayaca ait grafikleri görüntüleyebilirsiniz.


Uygulamanızı uygulamayı ve verileri toplamayı tamamladıktan sonra, daha ayrıntılı bir rapor için toplamayı durdurabilirsiniz. Bunu yapmak için **koleksiyonu durdur** düğmesine basın.


Rapor yüklendikten sonra, aşağıda gösterilene benzer bir sonlandırılmış rapor görmeniz gerekir.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text=".NET sayaç aracı raporu.":::

Rapor, aşağıdaki değerleri gösterir:

- Min-seçili zaman aralığında bu sayacın en küçük değeri.
- Max-seçili zaman aralığında bu sayaç için en büyük değer.
- Average-seçili zaman aralığında bu sayacın ortalama değeri.

Sütun başlıklarına sağ tıklayıp bir başlık seçerek tablodaki sütunları filtreleyebilir veya ekleyebilirsiniz.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text=".NET sayacı araç sütunları.":::

Ayrıca, sayaçlar ' ın yanındaki onay kutularını seçerek ayrıntılı rapordaki grafikleri görüntüleyebilirsiniz. Tablolardaki veriler, toplanan izlemenin tüm süresinin varsayılan olarak değerini temsil eder. Verileri belirli bir zaman aralığına göre filtrelemek için, grafiklere tıklayın ve sürükleyin.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text=".NET sayaçları aracı zaman filtreleme.":::

Tablo, grafiklerde seçilen süre için ilgili değerlere güncelleştirilir. Seçili zaman aralığını tüm izlemeye sıfırlamak için **Seçimi temizle** düğmesini kullanın.


## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)
- [DotNet sayaçları](/dotnet/core/diagnostics/dotnet-counters)
