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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4467d2a885f4076461110fe288b4e80169158ede
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877102"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
**Iş parçacıkları** sekmesindeki **GPU etkinliği (sayfalama)** kesimleri, GPU 'nun disk belleği isteklerini işleme süresini temsil eder.  Bir segmentin uzunluğu, GPU 'nun doğrudan bellek erişimi (DMA) disk belleği paketini işleme süresini temsil eder. Genellikle disk belleği paketleri CPU ve GPU arasında bellek aktarımıyla ilişkilendirilir.

 Bir GPU disk belleği segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu, DirectX altyapısıyla ilişkili donanım kuyruğunda bekleme süresini, DMA paketini gönderen işlemi ve paketi işlemek için gereken süreyi içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)