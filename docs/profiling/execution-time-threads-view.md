---
title: Yürütme Süresi (İş Parçacığı Görünümü) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969920"
---
# <a name="execution-time-threads-view"></a>Yürütme süresi (İş Parçacığı Görünümü)
İş Parçacığı Görünümü zaman çizelgesindeki bu kesimler, iş parçacığının sistemdeki mantıksal bir çekirdek üzerinde etkin bir şekilde çalışma yaptığı yürütme süresini temsil eder.

 İş parçacığı durumundaki değişiklikler çekirdek bağlam geçiş olayları aracılığıyla algılanır. Windows için Olay İzleme (ETW) her milisaniyede bir örnek yığınları yakalar. Çok kısa yeşil bir segmentte, hiçbir örnek alınması mümkündür. Bu nedenle, bazı kısa yürütme segmentleri hiçbir çağrı yığını gösterebilir.

 Bir yürütme kesimini tıklattığınızda, Eşzamanlılık Görselleştiricisi, tıklamanın konumuna en yakın örnek yığını görüntüler. Bu örnek yığının konumu, zaman çizelgesinin üzerinde siyah bir ok veya bakım ile gösterilir ve örnek yığını **Geçerli** sekmesinde görüntülenir.

 Geçerli görünümdeki tüm yürütme bölümleri için geleneksel bir örnekleme profili görmek için Görünür Zaman Çizelgesi Profili'nde **Yürütme'yi** tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme Profil Raporu](../profiling/execution-profile-report.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)