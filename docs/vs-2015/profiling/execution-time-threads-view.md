---
title: Yürütme süresi (Iş parçacıkları görünümü) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179037"
---
# <a name="execution-time-threads-view"></a>Yürütme Zamanı (İş Parçacıkları Görünümü)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacığı görünümü zaman çizelgesi içindeki bu segmentler, iş parçacığının sistemdeki bir mantıksal çekirdek üzerinde etkin bir şekilde iş yaptığı durumlarda yürütme süresini temsil eder.  
  
 İş parçacığı durumundaki değişiklikler çekirdek bağlam anahtarı olayları aracılığıyla algılanır. Windows için olay Izleme (ETW), her milisaniyelik örnek yığınları yakalar. Çok kısa bir yeşil kesimde, hiçbir örnek alınmadığından mümkündür. Bu nedenle, bazı kısa yürütme kesimleri hiçbir çağrı yığını göstermez.  
  
 Bir yürütme segmentine tıkladığınızda, eşzamanlılık görselleştiricisi tıklama konumuna en yakın örnek yığını görüntüler. Bu örnek yığının konumu, zaman çizelgesinin üstünde bir siyah ok veya şapka işareti ile gösterilir ve örnek yığın **geçerli** sekmede görüntülenir.  
  
 Geçerli görünümdeki tüm yürütme kesimleri için geleneksel bir örnekleme profilini görmek için, görünür zaman çizelgesi profilinde **yürütme** ' ye tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme profili raporu](../profiling/execution-profile-report.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
