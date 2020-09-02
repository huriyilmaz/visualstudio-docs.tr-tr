---
title: GPU etkinliği (diğer süreçler) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a502590c20fce1455d9259ae681178d9cd48e33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969508"
---
# <a name="gpu-activity-other-processes"></a>GPU Etkinliği (Diğer İşlemler)
Eşzamanlılık görselleştiricisi Iş parçacıkları görünümündeki **GPU etkinliği (diğer işlemler)** KESIMLERI, GPU 'nun sistemdeki diğer işlemler adına istekleri işleme süresini temsil eder. Bu istekler GPU 'YU doğrudan bellek erişimi (DMA) paketleri olarak gönderilir.  Bir segmentin uzunluğu, paketin GPU tarafından işlendiği süreyi temsil eder.

 Bu tür bir segment seçtiğinizde, **geçerli** sekmedeki rapor işlenen paket hakkındaki bilgileri görüntüler.  Bu bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğu, paketi gönderen işlem ve paketi işlemek için gereken süre içinde beklediğini gösteren süreyi içerir.