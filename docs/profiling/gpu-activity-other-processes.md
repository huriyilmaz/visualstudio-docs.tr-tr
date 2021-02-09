---
title: GPU etkinliği (diğer süreçler) | Microsoft Docs
description: Eşzamanlılık görselleştiricisi Iş parçacıkları görünümündeki GPU etkinliği (diğer süreçler) kesimleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e57d40910dfdff9b2eb1d5a9db76bac6ec8657d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907247"
---
# <a name="gpu-activity-other-processes"></a>GPU Etkinliği (Diğer İşlemler)
Eşzamanlılık görselleştiricisi Iş parçacıkları görünümündeki **GPU etkinliği (diğer işlemler)** KESIMLERI, GPU 'nun sistemdeki diğer işlemler adına istekleri işleme süresini temsil eder. Bu istekler GPU 'YU doğrudan bellek erişimi (DMA) paketleri olarak gönderilir.  Bir segmentin uzunluğu, paketin GPU tarafından işlendiği süreyi temsil eder.

 Bu tür bir segment seçtiğinizde, **geçerli** sekmedeki rapor işlenen paket hakkındaki bilgileri görüntüler.  Bu bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğu, paketi gönderen işlem ve paketi işlemek için gereken süre içinde beklediğini gösteren süreyi içerir.