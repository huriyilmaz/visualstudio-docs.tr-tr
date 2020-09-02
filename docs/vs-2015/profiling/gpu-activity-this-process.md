---
title: GPU etkinliği (Bu Işlem) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b616e307b3c42b09662be3fdad290ea9f740637c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434156"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi içindeki Iş parçacıkları görünümündeki **GPU etkinliği (Bu işlem)** KESIMLERI, GPU 'nun geçerli işlem adına istekleri işleme süresini temsil eder. Bu istekler, GPU 'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir. Bir segmentin uzunluğu, GPU 'nun geçerli işlem adına bir DMA paketi işlediği süreyi temsil eder.  
  
 GPU etkinlik segmentini seçtiğinizde, **geçerli** sekmedeki rapor işlenen DMA paketi hakkındaki bilgileri görüntüler. Bu bilgiler, paketin DirectX altyapısı, paketi gönderen işlem ve paketi işlemek için gereken süre ile ilişkili donanım kuyruğunda bekleme süresini içerir. Geçerli işlemden farklı bir işlem, DMA paketini fiziksel olarak GPU 'ya göndermiş olabilir. Eşzamanlılık görselleştiricisi, diğer bir işlemin geçerli işlem adına GPU 'ya ne zaman iş gönderirse tespit edebilir.
