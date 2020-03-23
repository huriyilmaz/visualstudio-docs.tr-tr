---
title: 'Nasıl Yapılır: Toplama Yöntemlerini Seçin | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c633e12b2e0bf157ffd94ef06a5898fdc3ec830
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776351"
---
# <a name="how-to-choose-collection-methods"></a>Nasıl yapılır: Toplama yöntemlerini seçin

Visual Studio Profil Oluşturma Araçları performans verilerini toplamanın üç yöntemini destekler: örnekleme, enstrümantasyon ve eşzamanlılık. .NET bellek ayırma ve yaşam boyu verilerini toplamak için örnekleme veya enstrümantasyon yöntemini de kullanabilirsiniz.

Uygulamanız için en uygun toplama yöntemini belirtmek için performans oturumu **Yöntemi** özelliğini kullanabilirsiniz. Toplama yöntemini Performans Sihirbazı, Performans Gezgini veya performans oturumunun özellik sayfalarından ayarlayabilirsiniz. Komut satırı araçlarını kullanıyorsanız, daha fazla bilgi için [Komut Satırı'ndan Profil Oluşturma'ya](../profiling/using-the-profiling-tools-from-the-command-line.md) bakın.

## <a name="performance-wizard"></a>Performans Sihirbazı

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Performans Sihirbazı'nı kullanarak bir toplama yöntemi seçmek için

- Sihirbazın ilk sayfasında aşağıdaki seçeneklerden birini seçin:

| Seçenek | Açıklama |
|----------------------------| - |
| **CPU Örneklemesi** | İlk çözümleme ve CPU kullanım sorunlarını çözümleme için yararlı olan uygulama istatistikleritoplar. |
| **Araçları** | Odaklanmış analiz ve girdi/çıktı performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verileri toplar. |
| **.NET Bellek Tahsisi** | .NET Framework bellek ayırma verilerini örnekleme profil oluşturma yöntemini kullanarak toplar. |
| **Eşzamanlılık** | Sayısal kaynak çekişme verileri toplar. |

## <a name="performance-explorer"></a>Performans Gezgini

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Performance Explorer'ı kullanarak bir toplama yöntemi seçmek için

1. Performans **Gezgini** araç çubuğunda, **Yöntem** açılır listesinin yanındaki oku tıklatın.

2. Tercih ettiğiniz toplama yöntemini tıklatın.

## <a name="performance-session-property-pages"></a>Performans Oturumu Özellik Sayfaları

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak örnekleme veya enstrümantasyon yöntemini seçmek için

1. **Performans Gezgini'nde**performans oturumunu seçin.

     Performans oturumu dosya adı . *psess* uzantısı.

2. Performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

3. Özellik **Sayfalarında,** **Genel'i**tıklatın.

4. Tercih ettiğiniz toplama yöntemini tıklatın.

    - Örnekleme verileri toplarken kullanılabilen diğer seçenekler hakkında bilgi için [bkz.](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Örnekleme verileri toplarken kullanılabilen diğer seçenekler hakkında bilgi için [bkz.](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak .NET bellek veri toplamayı seçmek için

1. **Performans Gezgini'nde**performans oturumunu seçin.

     Performans oturumu dosya adı .psess uzantısı vardır.

2. Performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

3. Özellik **Sayfalarında,** **Genel'i**tıklatın.

4. **Örnekleme** veya **Enstrümantasyon'u**tıklatın.

5. .NET Framework nesne ayırmalarının boyutunu ve sayısını toplamak için **.NET nesne ayırma bilgilerini topla'yı** tıklatın.

6. (İsteğe bağlı) Nesne belleği geri alındı çöp toplama nesilleri hakkında veri toplamak için **.NET nesne yaşam boyu bilgilerini de tıklatın.**

     .NET bellek verilerini toplarken kullanılabilen diğer seçenekler hakkında bilgi için [bkz.](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak eşzamanlılık veri toplamayı seçmek için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Özellik **Sayfalarında,** **Genel'i**tıklatın.

3. **Eşzamanlılık'ı**tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma Örnekleme[veri değerlerini](../profiling/understanding-sampling-data-values.md)
anlama[Performans oturumu özellikleri](../profiling/performance-session-properties.md)
