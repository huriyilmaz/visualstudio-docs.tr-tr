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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9b57a0aa799bd3793b38a7cbad60b0aba6176b48aaed1e7c46c9f733b95daadf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410209"
---
# <a name="synchronization-time"></a>Eşitleme saati
Zaman çizelgesindeki bu segmentler, eşitleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bir iş parçacığı eşitlemede engellenmiş olarak işaretlendiğinde, bunlardan biri kapsanır:

- İş parçacığının yürütülmesi, veya gibi iyi bilinen bir iş parçacığı eşitleme API 'sine çağrı ile sonuçlanmasına neden olmuş olabilir `EnterCriticalSection()` `WaitForSingleObject()` .

- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle, çağrı yığınında bir çerçeve bu kategoriye eşlenmiş temel bir çekirdek engelleme temel değerine ulaştığından, diğer kategorilere eşlenebilen bazı API 'Ler eşitleme olarak da görünebilir.

  Bir iş parçacığı engelleme olayının temel nedenini anlamak için engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)