---
title: GPU etkinliği (diğer süreçler) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434143"
---
# <a name="gpu-activity-other-processes"></a>GPU Etkinliği (Diğer İşlemler)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi Iş parçacıkları görünümündeki **GPU etkinliği (diğer işlemler)** KESIMLERI, GPU 'nun sistemdeki diğer işlemler adına istekleri işleme süresini temsil eder. Bu istekler GPU 'YU doğrudan bellek erişimi (DMA) paketleri olarak gönderilir.  Bir segmentin uzunluğu, paketin GPU tarafından işlendiği süreyi temsil eder.  
  
 Bu tür bir segment seçtiğinizde, **geçerli** sekmedeki rapor işlenen paket hakkındaki bilgileri görüntüler.  Bu bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğu, paketi gönderen işlem ve paketi işlemek için gereken süre içinde beklediğini gösteren süreyi içerir.
