---
title: Bellek yönetimi zamanı | Microsoft Docs
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
ms.openlocfilehash: 442973edb18e75bafda8a9397eac799286c69dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62963787"
---
# <a name="memory-management-time"></a>Bellek yönetimi zamanı
Zaman çizelgesindeki bu segmentler, bellek yönetimi olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu senaryo, bir iş parçacığının sayfalama gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellendiğini gösterir. Bu süre boyunca, concurrency Visualizer 'ın bellek yönetimi olarak sayışında bir API veya çekirdek durumunda bir iş parçacığı engellenmiştir. Bunlar, sayfalama ve bellek ayırma gibi olayları içerir.

 Bellek yönetimi olarak sınıflandırılan blokların temel nedenlerini daha iyi anlamak için ilişkili çağrı yığınlarını ve profil raporlarını inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)