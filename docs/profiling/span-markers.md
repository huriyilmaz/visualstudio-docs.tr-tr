---
title: Yayılma Işaretçileri | Microsoft Docs
description: Bir yayılma işaretinin bir uygulamanın anlamlı bir aşamasını nasıl temsil ettiğini öğrenin ve eşzamanlılık görselleştiricisi içindeki bir yayılımı gösteren bir örnek görürsünüz.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 98fc9241a8f0bdcf4b92dfd4f1f745a1bfc8ea4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141538"
---
# <a name="span-markers"></a>Aralık işaretçileri
Yayılma işareti, bir uygulamanın anlamlı bir aşamasını temsil eder. Örneğin, belirli bir iş öğesinin işlendiği zaman aralığını temsil eden bir Aralık kullanabilirsiniz. Uzunluğu, ilgili uygulama aşamasının süresini temsil eder. Bu çizimde eşzamanlılık görselleştiricisi içindeki bir yayılma gösterilmektedir:

 ![Eşzamanlılık görselleştiricisi Içindeki bir span işaretleyicisi](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Eşzamanlılık görselleştiricisi içindeki bir span işaretleyicisi

## <a name="span-category"></a>Span kategorisi
 Bir span işaretleyicisi, kategorisine bağlı olarak beş farklı renkten birinde görüntülenir. Beş taneden fazla kategori varsa renkler yinelenir. Kategori herhangi bir tamsayı olabilir. Bu resimde olası beş renk gösterilmektedir:

 ![Farklı kategorilerdeki beş yayılma](../profiling/media/cvmarkerspancategory.png "Cvmarkerspankategorisi") İlk beş yayılma kategorisinin renkleri

## <a name="span-aggregation-markers"></a>Yayılma toplama işaretçileri
 Bazı durumlarda, eşzamanlılık görselleştiricisi içinde ayrı olarak çiziledikleri bir diğeri için bir Aralık işaretçileri oluşur. Bu gerçekleştiğinde, temel alınan yayılmaları temsil eden bir gri *yayılma toplama işaretleyicisi* gösterilir. İşaretçiyi Bu simgelerden birine bıraktığınızda, bir araç ipucu temsil edilen temeldeki yayılmalar sayısını görüntüler. Yayılmaları görüntülemek için yakınlaştırın. Tüm yolu yakınlaştırıp yine de bir yayılma toplama işaretçisi alırsanız, [Işaretçiler raporundaki](../profiling/markers-report.md)temel alınan Aralık işaretçilerini görüntüleyebilirsiniz. Bu çizimde bir span toplama işaretçisi gösterilmektedir:

 ![Eşzamanlılık görselleştiricisi içinde toplam yayılma işaretçisi](../profiling/media/cvmarkerspanaggregate.png "Cvmarkerspantoplama") Bir span toplama işaretleyicisi

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md)
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)