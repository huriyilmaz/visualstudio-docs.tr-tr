---
title: Yayılma İşaretleyicileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69b48a5b1b551e2e29b9aa10e7f68ff0df0e379
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62980992"
---
# <a name="span-markers"></a>Yayılma işaretleri
Yayılma işaretçisi, uygulamanın anlamlı bir aşamasını temsil eder. Örneğin, belirli bir çalışma öğesinin işlendiği bir zaman aralığını temsil etmek için bir yayılma alanı kullanabilirsiniz. Uzunluğu, ilgili uygulama aşamasının süresini gösterir. Bu resimde Eşzamanlılık Görselleştiricisi'nde bir yayılma gösterir:

 ![Eşzamanlılık Görselleştiricisi'nde bir yayılma işareti](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Eşzamanlılık Görselleştiricisi'nde bir yayılma işareti

## <a name="span-category"></a>Yayılma alanı kategorisi
 Bir yayılma işareti, kategorisine bağlı olarak beş farklı renkte görüntülenir. Beşten fazla kategori varsa renkler yinelenir. Kategori herhangi bir sonda olabilir. Bu resimde beş olası renk gösterilmektedir:

 ![Farklı kategorilerde beş açıklık](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") İlk beş açıklık kategorisinin renkleri

## <a name="span-aggregation-markers"></a>Yayılma agrega işaretleri
 Bazen yayılma işaretçileri Eşzamanlılık Görselleştiricisinde birbirine o kadar yakın olur ki tek tek çizilemezler. Bu durumda, temel açıklıkları temsil eden gri bir *yayılma işareti* gösterilir. İşaretçiyi bu simgelerden birine dayadığınızda, bir araç ucu temsil edilen temel yayılma sayısını görüntüler. Yayılma açıklıklarını görüntülemek için yakınlaştırın. Tüm yol yakınlaştırır ve hala bir yayılma ağıl işaretçisi alırsanız, [Işaretçiler Raporu'nda](../profiling/markers-report.md)temel yayılma işaretçilerini görüntüleyebilirsiniz. Bu resimde bir yayılma işareti gösterir:

 ![EşzamanlıLık Görselleştiricisi'nde bir toplam yayılma işareti](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Bir yayılma toplama işaretçisi

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlı Görselleştirici işaretleri](../profiling/concurrency-visualizer-markers.md)
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)