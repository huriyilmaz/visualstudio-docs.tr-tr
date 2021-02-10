---
title: Eşitleme saati | Microsoft Docs
description: Zaman çizelgesindeki segmentlerin eşitleme olarak sınıflandırılan engelleme süreleriyle nasıl ilişkilendirildiğini öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: b6469c1020f125dd28798ad4bff5ccc9d3e7aa06
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949382"
---
# <a name="synchronization-time"></a>Eşitleme saati
Zaman çizelgesindeki bu segmentler, eşitleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bir iş parçacığı eşitlemede engellenmiş olarak işaretlendiğinde, bunlardan biri kapsanır:

- İş parçacığının yürütülmesi, veya gibi iyi bilinen bir iş parçacığı eşitleme API 'sine çağrı ile sonuçlanmasına neden olmuş olabilir `EnterCriticalSection()` `WaitForSingleObject()` .

- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle, çağrı yığınında bir çerçeve bu kategoriye eşlenmiş temel bir çekirdek engelleme temel değerine ulaştığından, diğer kategorilere eşlenebilen bazı API 'Ler eşitleme olarak da görünebilir.

  Bir iş parçacığı engelleme olayının temel nedenini anlamak için engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)