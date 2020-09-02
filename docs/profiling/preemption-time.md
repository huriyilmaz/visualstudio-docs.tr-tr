---
title: Önalım saati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935899"
---
# <a name="preemption-time"></a>Önalım zamanı
Zaman çizelgesindeki bu segmentler, ön işleme olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Bu kategori, bir iş parçacığının şu nedenlerden biri nedeniyle dışarı geçmiş olduğunu gösterir:

- Zamanlayıcı, daha yüksek öncelikli bir iş parçacığı kullanarak bunu değiştirdi.

- İş parçacığının yürütme doacıı ve diğer iş parçacıkları yürütülmeye hazırlanıyor.

  Bu süre boyunca bir iş parçacığı, eşzamanlılık görselleştiricinin ön çıkarma olarak saymasının bir çekirdek bekleme nedeni ile engellenmiştir. Ön işleme kesimleri, bir iş parçacığı mantıksal bir çekirdeğin dışına gönderildiğinde başlar ve bu iş parçacığı yürütmeyi sürdürürse biter.

  Önceden önleyici bir segmentin araç ipucu, ön işleme neden olan işlemin veya iş parçacığının adını görüntüler. Ancak, bunun yerine geçen işlem veya iş parçacığının, aslında geçersiz bir süre boyunca Çalıştırıldığın göstermez.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)