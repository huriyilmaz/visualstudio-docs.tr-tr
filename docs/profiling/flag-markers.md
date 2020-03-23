---
title: Bayrak İşaretleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccc0c7aa3386e906ad13331a596953db70240701
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969985"
---
# <a name="flag-markers"></a>Bayrak işaretleri
Bayrak işaretçisi, uygulamada bir anda meydana gelen bir şeyi temsil eder. Bayrak birçok türde uygulama olayını temsil edebilir. Örneğin, bir bayrak, belirli bir çalışma öğesinin zamanlandığında veya özel bir özel durum atıldığında gösterilebilir. Görev Paralel Kitaplığı gibi çalışma saatleri de bayraklar oluşturabilir.

## <a name="flag-importance"></a>Bayrak önemi
 Bayraklar, önemlerine bağlı olarak farklı boyutlarda görüntülenir. Herhangi bir işaretçi gibi, önemi düşük, normal, yüksek veya kritik olabilir.  Bu resimde önem düzeyine göre işaretçilerin görünümünü gösterir:

 ![Düşük, Normal, Yüksek ve Kritik Önem belirteçleri](../profiling/media/cvmarkerimportance.png "CVMarkerÖnemi") Bayrak önemini gösteren işaretçiler

## <a name="flag-category"></a>Bayrak kategorisi
 Bir bayrak, kategorisine bağlı olarak beş farklı renkte görüntülenir. Beşten fazla kategori varsa renkler yeniden kullanılır. Rengi seçemezsiniz. Herhangi bir işaretçi gibi, kategori herhangi bir sonda olabilir. Sonraki resimde ilk beş kategorinin renkleri gösterilmektedir.

 ![Kategori işaretçilerinin beş rengi](../profiling/media/cvmarkercategory.png "CVMarkerKategorisi") Kategorileri gösteren işaretçiler

## <a name="alerts"></a>Uyarılar
 Uyarı, özel durum gibi kritik bir uygulama olayını temsil eden kırmızı renkli bir bayraktır.  İşte bir uyarı:

 ![Eşzamanlı Görselleştirici Uyarı İşaretleyicisi](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Bir uyarı işaretçisi

## <a name="aggregation-flags"></a>Toplama bayrakları
 Bazen eşpara birimi görselinde bayraklar birbirine o kadar yakın olur ki tek tek çizilemezler. Bu durumda, temel bayrakları temsil eden gri bir *toplama bayrağı* gösterilir. İşaretçiyi bu simgelerden birine dayadığınızda, bir araç ucu temsil edilen temel bayrakların sayısını görüntüler. Bayrakları görüntülemek için yakınlaştırın. Tüm yolu yakınlaştırır ve yine de bir toplama bayrağı alırsanız, [İşaretçiler Raporu'nda](../profiling/markers-report.md)temel bayrakları görüntüleyebilirsiniz.

 Toplama bayrakları farklı boyutlarda çizilir. Boyutu toplama en önemli bayrağın önem düzeyine bağlıdır. Aşağıdaki resimde, toplama bayrakları artan önem sırasına göre gösterilmektedir.

 ![Dört önem düzeyi gösteren toplu bayraklar](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Önem düzeyine göre toplama bayrakları

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlı Görselleştirici işaretleri](../profiling/concurrency-visualizer-markers.md)
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)