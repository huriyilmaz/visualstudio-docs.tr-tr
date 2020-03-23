---
title: GPU Etkinliği (Sayfalama) | Microsoft Dokümanlar
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
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969621"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
**İş parçacıkları** sekmesindeki **GPU Etkinliği (Sayfalama)** segmentleri, GPU'nun sayfalama isteklerini işlediğindeki zamanları temsil eder.  Bir kesimin uzunluğu, GPU'nun doğrudan bellek erişimi (DMA) çağrı paketini işleme sayılma süresini gösterir. Genellikle, sayfalama paketleri CPU ve GPU arasında bellek transferi ile ilişkilidir.

 Bir GPU sayfalama kesimi seçtiğinizde, **Geçerli** sekmesindeki rapor işlenen DMA paketi yle ilgili bilgileri görüntüler. Buna DirectX altyapısıyla ilişkili donanım kuyruğunda beklediği süre, DMA paketini gönderen işlem ve paketi işlemek için gereken süre dahildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)