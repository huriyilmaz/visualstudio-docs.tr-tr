---
title: GPU etkinliği (sayfalama) | Microsoft Docs
description: Eşzamanlılık görselleştiricinin Iş parçacıkları sekmesindeki GPU etkinliği (sayfalama) segmentlerini gözden geçirin. Segmentler, GPU 'nun disk belleği isteklerini işleme süresini temsil eder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bdf1fcffad90155baba8f92d11e31d1b316710b
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801189"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
**Iş parçacıkları** sekmesindeki **GPU etkinliği (sayfalama)** kesimleri, GPU 'nun disk belleği isteklerini işleme süresini temsil eder.  Bir segmentin uzunluğu, GPU 'nun doğrudan bellek erişimi (DMA) disk belleği paketini işleme süresini temsil eder. Genellikle disk belleği paketleri CPU ve GPU arasında bellek aktarımıyla ilişkilendirilir.

 Bir GPU disk belleği segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu, DirectX altyapısıyla ilişkili donanım kuyruğunda bekleme süresini, DMA paketini gönderen işlemi ve paketi işlemek için gereken süreyi içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)