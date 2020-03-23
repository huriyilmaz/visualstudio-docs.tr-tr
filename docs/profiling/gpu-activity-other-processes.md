---
title: GPU Etkinliği (Diğer Süreçler) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969508"
---
# <a name="gpu-activity-other-processes"></a>GPU Etkinliği (Diğer İşlemler)
Eşzamanlılık Görselleştiricisinin İş Parçacıkları görünümündeki **GPU Etkinliği (Diğer İşlemler)** segmentleri, GPU'nun sistemdeki diğer işlemler adına istekleri işlediği zamanları temsil eder. Bu istekler GPU'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir.  Bir kesimin uzunluğu, paketin GPU tarafından işlendiği süreyi gösterir.

 Bu tür bir kesimi seçtiğinizde, **Geçerli** sekmesindeki rapor işlenen paketle ilgili bilgileri görüntüler.  Bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğunda beklediği süreyi, paketi gönderen işlemi ve paketi işlemek için gereken süreyi içerir.