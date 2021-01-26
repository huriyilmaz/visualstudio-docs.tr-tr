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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcfc96f9b29b8fae3bf9a97273ed6c675d1655fb
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801176"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
Eşzamanlılık görselleştiricisi içindeki Iş parçacıkları görünümündeki **GPU etkinliği (Bu işlem)** KESIMLERI, GPU 'nun geçerli işlem adına istekleri işleme süresini temsil eder. Bu istekler, GPU 'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir. Bir segmentin uzunluğu, GPU 'nun geçerli işlem adına bir DMA paketi işlediği süreyi temsil eder.

 GPU etkinlik segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu bilgiler, paketin DirectX altyapısı, paketi gönderen işlem ve paketi işlemek için gereken süre ile ilişkili donanım kuyruğunda bekleme süresini içerir. Geçerli işlemden farklı bir işlem, DMA paketini fiziksel olarak GPU 'ya göndermiş olabilir. Eşzamanlılık görselleştiricisi, diğer bir işlemin geçerli işlem adına GPU 'ya ne zaman iş gönderirse tespit edebilir.