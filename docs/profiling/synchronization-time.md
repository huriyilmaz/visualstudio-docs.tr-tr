---
title: Eşitleme saati | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62965316"
---
# <a name="synchronization-time"></a>Eşitleme saati
Zaman çizelgesindeki bu segmentler, eşitleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bir iş parçacığı eşitlemede engellenmiş olarak işaretlendiğinde, bunlardan biri kapsanır:

- İş parçacığının yürütülmesi, veya gibi iyi bilinen bir iş parçacığı eşitleme API 'sine çağrı ile sonuçlanmasına neden olmuş olabilir `EnterCriticalSection()` `WaitForSingleObject()` .

- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle, çağrı yığınında bir çerçeve bu kategoriye eşlenmiş temel bir çekirdek engelleme temel değerine ulaştığından, diğer kategorilere eşlenebilen bazı API 'Ler eşitleme olarak da görünebilir.

  Bir iş parçacığı engelleme olayının temel nedenini anlamak için engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)