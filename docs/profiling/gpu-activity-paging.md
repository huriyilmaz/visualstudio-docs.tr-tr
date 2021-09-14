---
title: GPU Etkinliği (Disk Belleği) | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nin İş Parçacıkları sekmesinde GPU Etkinliği (Sayfalama) kesimlerini gözden geçirme. Segmentler, GPU'nun disk belleği isteklerini işleme zamanlarını temsil eder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f2ec6ebfde3a8f205e3a515c70930a1344598c9b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634374"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
İş **Parçacıkları sekmesindeki GPU Etkinliği (Sayfalama)** **segmentleri,** GPU'nun disk belleği isteklerini işleme zamanlarını temsil eder.  Bir kesimin uzunluğu, GPU'nun doğrudan bellek erişimi (DMA) disk belleği paketini işleme süresini temsil eder. Genellikle, disk belleği paketleri CPU ve GPU arasında bellek aktarımıyla ilişkilendirilir.

 Gpu disk belleği segmentini seçerek Geçerli **sekmesindeki rapor,** işlenen DMA paketiyle ilgili bilgileri görüntüler. Buna DirectX altyapısıyla ilişkili donanım kuyruğunda beklediği süre, DMA paketini göndererek gönderilen işlem ve paketin iş için gereken süre dahildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)