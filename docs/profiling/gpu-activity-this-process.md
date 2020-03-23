---
title: GPU Etkinliği (Bu İşlem) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68e85fc44977a3d9756965de12e25d13d62dbb89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969544"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
Eşzamanlılık Görselleştiricisi'ndeki İş Parçacıkları görünümündeki **GPU Etkinliği (Bu İşlem)** segmentleri, GPU'nun geçerli işlem adına istekleri işlediği zamanları temsil eder. Bu istekler doğrudan bellek erişimi (DMA) paketleri olarak GPU'ya gönderilir. Bir kesimin uzunluğu, GPU'nun geçerli işlem adına bir DMA paketini işlediği zamanı gösterir.

 GPU etkinlik kesimini seçtiğinizde, **Geçerli** sekmesindeki rapor işlenen DMA paketi yle ilgili bilgileri görüntüler. Bu bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğunda beklediği süreyi, paketi gönderen işlemi ve paketi işlemek için gereken süreyi içerir. Geçerli işlem dışındaki bir işlem DMA paketini fiziksel olarak GPU'ya göndermiş olabilir. Eşzamanlılık Görselleştiricisi, başka bir işlemin geçerli işlem adına GPU'ya ne zaman iş gönderdiğini algılayabilir.