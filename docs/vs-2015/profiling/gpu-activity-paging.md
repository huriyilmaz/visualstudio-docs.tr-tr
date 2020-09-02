---
title: GPU etkinliği (sayfalama) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434169"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Iş parçacıkları sekmesindeki **GPU etkinliği (sayfalama)** KESIMLERI, GPU 'nun disk belleği isteklerini işleme süresini temsil eder.  Bir segmentin uzunluğu, GPU 'nun doğrudan bellek erişimi (DMA) disk belleği paketini işleme süresini temsil eder. Genellikle disk belleği paketleri CPU ve GPU arasında bellek aktarımıyla ilişkilendirilir.  
  
 Bir GPU disk belleği segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu, DirectX altyapısıyla ilişkili donanım kuyruğunda bekleme süresini, DMA paketini gönderen işlemi ve paketi işlemek için gereken süreyi içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Görünümü](../profiling/utilization-view.md)
