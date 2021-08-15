---
title: GPU etkinliği (Bu Işlem) | Microsoft Docs
description: Eşzamanlılık görselleştiricisi Iş parçacığı görünümündeki GPU etkinliği (Bu Işlem) kesimleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f4396b1feecfe343cf3dbdf1ad9d7aa2b749fcfb7e362fb13270563c6087e9a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121246532"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
Eşzamanlılık görselleştiricisi içindeki Iş parçacıkları görünümündeki **GPU etkinliği (Bu işlem)** KESIMLERI, GPU 'nun geçerli işlem adına istekleri işleme süresini temsil eder. Bu istekler, GPU 'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir. Bir segmentin uzunluğu, GPU 'nun geçerli işlem adına bir DMA paketi işlediği süreyi temsil eder.

 GPU etkinlik segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu bilgiler, paketin DirectX altyapısı, paketi gönderen işlem ve paketi işlemek için gereken süre ile ilişkili donanım kuyruğunda bekleme süresini içerir. Geçerli işlemden farklı bir işlem, DMA paketini fiziksel olarak GPU 'ya göndermiş olabilir. Eşzamanlılık görselleştiricisi, diğer bir işlemin geçerli işlem adına GPU 'ya ne zaman iş gönderirse tespit edebilir.