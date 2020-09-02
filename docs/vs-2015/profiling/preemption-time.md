---
title: Önalım saati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198072"
---
# <a name="preemption-time"></a>Önalım Zamanı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaman çizelgesindeki bu segmentler, önalım olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Bu kategori, bir iş parçacığının şu nedenlerden biri nedeniyle dışarı geçmiş olduğunu gösterir:  
  
- Zamanlayıcı, daha yüksek öncelikli bir iş parçacığı kullanarak bunu değiştirdi.  
  
- İş parçacığının yürütme doacıı ve diğer iş parçacıkları yürütülmeye hazırlanıyor.  
  
  Bu süre boyunca, eşzamanlılık görselleştiricisi önalım olarak saymasının bir çekirdek bekleme nedeni tarafından bir iş parçacığı engellenmiştir. Önalım kesimleri, bir iş parçacığı mantıksal bir çekirdeğin dışına gönderildiğinde başlar ve bu iş parçacığı yürütmeyi devam ettirir.  
  
  Bir önden segment için araç ipucu, önalım neden olan işlemin veya iş parçacığının adını görüntüler. Ancak, bunun yerine geçen işlem veya iş parçacığının, aslında geçersiz bir süre boyunca Çalıştırıldığın göstermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
