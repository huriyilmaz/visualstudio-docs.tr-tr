---
title: Eşitleme Zamanı | Microsoft Docs
description: Zaman çizelgesinde segmentlerin Eşitleme olarak kategorilere ayrılmış engelleme zamanları ile nasıl ilişkilendirileceklerini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 118fa48f6c818c366d733fc29fbcc4a12883a6c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634334"
---
# <a name="synchronization-time"></a>Eşitleme zamanı
Zaman çizelgesinde yer alan bu segmentler, Eşitleme olarak kategorilere ayrılmış engelleme süreleri ile ilişkilendirilmektedir. Bir iş parçacığı eşitlemede engellenmiş olarak işaretlenirken, bunlardan biri örtük olarak işaretlenir:

- İş parçacığının yürütülmesi, veya gibi iyi bilinen bir iş parçacığı eşitleme API'sine çağrıyla `EnterCriticalSection()` sonuçlandırmış `WaitForSingleObject()` olabilir.

- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle diğer kategorilere eşlenmiş olan bazı API'ler de eşitleme olarak görünebilir çünkü çağrı yığınında bir çerçeve sonunda bu kategoriyle eşlenmiş temel çekirdek engelleme temellerine ulaşmış olur.

  Bir iş parçacığının engelleme olayına neden olan temel nedeni anlamak için engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)