---
title: Yayılma Işaretçileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f733ccec12e422a11532b8012836422d14d93b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198304"
---
# <a name="span-markers"></a>Kapsam İşaretleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yayılma işareti, bir uygulamanın anlamlı bir aşamasını temsil eder. Örneğin, belirli bir iş öğesinin işlendiği zaman aralığını temsil eden bir Aralık kullanabilirsiniz. Uzunluğu, ilgili uygulama aşamasının süresini temsil eder. Bu çizimde eşzamanlılık görselleştiricisi içindeki bir yayılma gösterilmektedir:  
  
 ![Eşzamanlılık görselleştiricisi içindeki bir span işaretleyicisi](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Eşzamanlılık görselleştiricisi içindeki bir span işaretleyicisi  
  
## <a name="span-category"></a>Span kategorisi  
 Bir span işaretleyicisi, kategorisine bağlı olarak beş farklı renkten birinde görüntülenir. Beş taneden fazla kategori varsa renkler yinelenir. Kategori herhangi bir tamsayı olabilir. Bu resimde olası beş renk gösterilmektedir:  
  
 ![Farklı kategorilerdeki beş yayılma](../profiling/media/cvmarkerspancategory.png "Cvmarkerspankategorisi")  
İlk beş yayılma kategorisinin renkleri  
  
## <a name="span-aggregation-markers"></a>Yayılma toplama Işaretçileri  
 Bazı durumlarda, eşzamanlılık görselleştiricisi içinde ayrı olarak çiziledikleri bir diğeri için bir Aralık işaretçileri oluşur. Bu gerçekleştiğinde, temel alınan yayılmaları temsil eden bir gri *yayılma toplama işaretleyicisi* gösterilir. İşaretçiyi Bu simgelerden birine bıraktığınızda, bir araç ipucu temsil edilen temeldeki yayılmalar sayısını görüntüler. Yayılmaları görüntülemek için yakınlaştırın. Tüm yolu yakınlaştırıp yine de bir yayılma toplama işaretçisi alırsanız, [Işaretçiler raporundaki](../profiling/markers-report.md)temel alınan Aralık işaretçilerini görüntüleyebilirsiniz. Bu çizimde bir span toplama işaretçisi gösterilmektedir:  
  
 ![Eşzamanlılık görselleştiricisi içinde toplam yayılma işaretçisi](../profiling/media/cvmarkerspanaggregate.png "Cvmarkerspantoplama")  
Bir span toplama işaretleyicisi  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi Işaretçileri](../profiling/concurrency-visualizer-markers.md)   
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
