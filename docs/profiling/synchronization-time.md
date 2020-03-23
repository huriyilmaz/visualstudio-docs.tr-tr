---
title: Senkronizasyon Süresi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62965316"
---
# <a name="synchronization-time"></a>Eşitleme süresi
Zaman çizelgesindeki bu kesimler, Eşitleme olarak kategorize edilen engelleme süreleri ile ilişkilidir. Bir iş parçacığı eşitleme üzerinde engellenmiş olarak işaretlendiğinde, şu konulardan biri ima edilir:

- İş parçacığının yürütülmesi gibi `EnterCriticalSection()` iyi bilinen bir iş parçacığı eşitleme API `WaitForSingleObject()`için bir çağrı neden olabilir veya .

- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle diğer kategorilerle eşlenebilir bazı API'ler de eşitleme olarak görünebilir, çünkü çağrı yığınındaki bir çerçeve sonunda temel bir çekirdek engelleme ilkel bu kategoriye eşlenir.

  İş parçacığı engelleme olayının altında yatan nedeni anlamak için, engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)