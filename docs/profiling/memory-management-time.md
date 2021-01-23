---
title: Bellek yönetimi zamanı | Microsoft Docs
description: Bu senaryonun, bir iş parçacığının sayfalama gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellenip engellenmediğini nasıl önleyeceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e1dd2868f5b29a12f3f54f46e5cb5833d270af
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721209"
---
# <a name="memory-management-time"></a>Bellek yönetimi zamanı
Zaman çizelgesindeki bu segmentler, bellek yönetimi olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu senaryo, bir iş parçacığının sayfalama gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellendiğini gösterir. Bu süre boyunca, concurrency Visualizer 'ın bellek yönetimi olarak sayışında bir API veya çekirdek durumunda bir iş parçacığı engellenmiştir. Bunlar, sayfalama ve bellek ayırma gibi olayları içerir.

 Bellek yönetimi olarak sınıflandırılan blokların temel nedenlerini daha iyi anlamak için ilişkili çağrı yığınlarını ve profil raporlarını inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)