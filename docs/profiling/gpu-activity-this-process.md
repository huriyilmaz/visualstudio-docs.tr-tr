---
title: GPU etkinliği (Bu Işlem) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969544"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
Eşzamanlılık görselleştiricisi içindeki Iş parçacıkları görünümündeki **GPU etkinliği (Bu işlem)** KESIMLERI, GPU 'nun geçerli işlem adına istekleri işleme süresini temsil eder. Bu istekler, GPU 'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir. Bir segmentin uzunluğu, GPU 'nun geçerli işlem adına bir DMA paketi işlediği süreyi temsil eder.

 GPU etkinlik segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu bilgiler, paketin DirectX altyapısı, paketi gönderen işlem ve paketi işlemek için gereken süre ile ilişkili donanım kuyruğunda bekleme süresini içerir. Geçerli işlemden farklı bir işlem, DMA paketini fiziksel olarak GPU 'ya göndermiş olabilir. Eşzamanlılık görselleştiricisi, diğer bir işlemin geçerli işlem adına GPU 'ya ne zaman iş gönderirse tespit edebilir.