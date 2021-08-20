---
title: Bayrak İşaretçileri | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nde bayrak Visual Studio hakkında bilgi öğrenin. Bayrak işareti, uygulama içinde anında meydana gelen bir şeyi temsil eder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bdc63b316f76ea048223af61a0822077d11c0b9e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150423"
---
# <a name="flag-markers"></a>Bayrak işaretçileri
Bayrak işareti, uygulama içinde anında meydana gelen bir şeyi temsil eder. Bayrak, birçok tür uygulama olaylarını temsil ediyor olabilir. Örneğin, bir bayrak belirli bir iş öğesinin zamanlandığı veya bir özel durumun ne zaman olduğunu gösterebilir. Görev Paralel Kitaplığı gibi çalışma zamanları da bayraklar üretebilirsiniz.

## <a name="flag-importance"></a>Bayrak önemi
 Bayraklar önemlerine bağlı olarak farklı boyutlarda görüntülenir. Herhangi bir işaretleyici gibi önem düşük, normal, yüksek veya kritik olabilir.  Bu çizimde, işaretleyicilerin önem düzeyine göre görünümü gösterilir:

 ![Düşük, Normal, Yüksek ve Kritik önem işaretleyicileri](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") Bayrak önemini gösteren işaretçiler

## <a name="flag-category"></a>Bayrak kategorisi
 Bayrak, kategorisine bağlı olarak beş farklı renkten biri olarak görüntülenir. Beşten fazla kategori varsa renkler yeniden kullanılır. Rengi seçesiniz. Herhangi bir işaretçi gibi kategori de herhangi bir tamsayı olabilir. Sonraki çizimde ilk beş kategorinin renkleri gösterilmiştir.

 ![Kategori işaretçilerinin beş rengi](../profiling/media/cvmarkercategory.png "CVMarkerCategory") Kategorileri gösteren işaretçiler

## <a name="alerts"></a>Uyarılar
 Uyarı, özel durum gibi kritik bir uygulama olayı temsil eden kırmızı renkli bir bayraktır.  Uyarı şu şekildedir:

 ![Eşzamanlılık Görselleştiricisi Uyarı İşaretçisi](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Uyarı işaretçisi

## <a name="aggregation-flags"></a>Toplama bayrakları
 Bazen Eşzamanlılık Görselleştiricisi'nde bayraklar birbirine çok yakın bir şekilde gerçekleşir ve bunlar tek tek çizilemez. Bu durum oluştuğunda, temel *alınan bayrakları temsil* eden gri bir toplama bayrağı gösterilir. İşaretçiyi bu simgelerden birinin üzerindeyken, bir araç ipucu temsil edilen temel bayrak sayısını görüntüler. Bayrakları görüntülemek için yakınlaştırın. Tüm yolu yakınlaştırıp yine de toplama bayrağını almaya devam ediyorsanız, temel alınan bayrakları İşaretçiler [Raporu'nde görüntüebilirsiniz.](../profiling/markers-report.md)

 Toplama bayrakları farklı boyutlarda çizilir. Boyut, toplamada en önemli bayrağın önem düzeyine bağlıdır. Aşağıdaki çizimde, artan önem sırasına sahip toplama bayrakları gösterilmiştir.

 ![Dört önem düzeyi gösteren toplam bayraklar](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Önem düzeyine göre toplama bayrakları

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md)
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)