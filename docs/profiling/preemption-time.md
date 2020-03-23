---
title: Preemption Zaman | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62935899"
---
# <a name="preemption-time"></a>Preemption süresi
Zaman çizelgesindeki bu kesimler, Ön alım olarak sınıflandırılan engelleme süresiyle ilişkilidir. Bu kategori, bir iş parçacığının şu nedenlerden biri nedeniyle kapatıldığı anlamına gelir:

- Zamanlayıcı daha yüksek bir öncelik iş parçacığı kullanarak yerini aldı.

- İş parçacığının yürütme kuantum süresi doldu ve diğer iş parçacıkları yürütmeye hazırdı.

  Bu süre zarfında, bir iş parçacığı Concurrency Visualizer Ön-emption olarak sayıyor bir çekirdek bekleme nedeni tarafından engellendi. Ön alım segmentleri, bir iş parçacığı mantıksal bir çekirdekten dışarı itildiğinde başlar ve bu iş parçacığı yürütmeye devam ettiğinde sona erer.

  Önceden boşaltılan bir kesimin araç ucu, ön boşalmaya neden olan işlemin veya iş parçacığının adını görüntüler. Ancak, bu, devralan işlemin veya iş parçacığının aslında önceden engellenen dönem boyunca işlediği anlamına gelmez.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)