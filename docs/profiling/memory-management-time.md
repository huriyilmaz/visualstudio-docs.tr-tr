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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f65a93962a3f742085b8b89b4d3117833b5b0985f2de9c8fef07255cb17bbcb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410482"
---
# <a name="memory-management-time"></a>Bellek yönetimi zamanı
Zaman çizelgesindeki bu segmentler, bellek yönetimi olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu senaryo, bir iş parçacığının sayfalama gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellendiğini gösterir. Bu süre boyunca, concurrency Visualizer 'ın bellek yönetimi olarak sayışında bir API veya çekirdek durumunda bir iş parçacığı engellenmiştir. Bunlar, sayfalama ve bellek ayırma gibi olayları içerir.

 Bellek yönetimi olarak sınıflandırılan blokların temel nedenlerini daha iyi anlamak için ilişkili çağrı yığınlarını ve profil raporlarını inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)