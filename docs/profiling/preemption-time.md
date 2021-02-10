---
title: Önalım saati | Microsoft Docs
description: Premption Time hakkında bilgi edinin ve zaman çizelgesindeki bu kesimlerin, ön işleme olarak sınıflandırılan engelleme süresi ile ilişkili olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8515043b228deb4fbcbf43c0e75b9826912f059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957328"
---
# <a name="preemption-time"></a>Önalım zamanı
Zaman çizelgesindeki bu segmentler, ön işleme olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Bu kategori, bir iş parçacığının şu nedenlerden biri nedeniyle dışarı geçmiş olduğunu gösterir:

- Zamanlayıcı, daha yüksek öncelikli bir iş parçacığı kullanarak bunu değiştirdi.

- İş parçacığının yürütme doacıı ve diğer iş parçacıkları yürütülmeye hazırlanıyor.

  Bu süre boyunca bir iş parçacığı, eşzamanlılık görselleştiricinin ön çıkarma olarak saymasının bir çekirdek bekleme nedeni ile engellenmiştir. Ön işleme kesimleri, bir iş parçacığı mantıksal bir çekirdeğin dışına gönderildiğinde başlar ve bu iş parçacığı yürütmeyi sürdürürse biter.

  Önceden önleyici bir segmentin araç ipucu, ön işleme neden olan işlemin veya iş parçacığının adını görüntüler. Ancak, bunun yerine geçen işlem veya iş parçacığının, aslında geçersiz bir süre boyunca Çalıştırıldığın göstermez.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)