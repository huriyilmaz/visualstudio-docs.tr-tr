---
title: Yürütme süresi (Iş parçacıkları görünümü) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0cf2a60fd194176b7cd9091f4e7dc7a758006f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969920"
---
# <a name="execution-time-threads-view"></a>Yürütme süresi (Iş parçacıkları görünümü)
İş parçacığı görünümü zaman çizelgesi içindeki bu segmentler, iş parçacığının sistemdeki bir mantıksal çekirdek üzerinde etkin bir şekilde iş yaptığı durumlarda yürütme süresini temsil eder.

 İş parçacığı durumundaki değişiklikler çekirdek bağlam anahtarı olayları aracılığıyla algılanır. Windows için olay Izleme (ETW), her milisaniyelik örnek yığınları yakalar. Çok kısa bir yeşil kesimde, hiçbir örnek alınmadığından mümkündür. Bu nedenle, bazı kısa yürütme kesimleri hiçbir çağrı yığını göstermez.

 Bir yürütme segmentine tıkladığınızda, eşzamanlılık görselleştiricisi tıklama konumuna en yakın örnek yığını görüntüler. Bu örnek yığının konumu, zaman çizelgesinin üstünde bir siyah ok veya şapka işareti ile gösterilir ve örnek yığın **geçerli** sekmede görüntülenir.

 Geçerli görünümdeki tüm yürütme kesimleri için geleneksel bir örnekleme profilini görmek için, görünür zaman çizelgesi profilinde **yürütme** ' ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme Profil Raporu](../profiling/execution-profile-report.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)