---
title: Bellek Yönetimi Süresi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62963787"
---
# <a name="memory-management-time"></a>Bellek yönetimi süresi
Zaman çizelgesindeki bu kesimler, Bellek Yönetimi olarak kategorize edilen engelleme süreleri ile ilişkilidir. Bu senaryo, bir iş parçacığı nın Paging gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellendiğini gösterir. Bu süre zarfında, EşzamanlıLık Görselleştiricisi bellek yönetimi olarak saydığı bir API veya çekirdek durumunda bir iş parçacığı engellendi. Bunlar, sayfalama ve bellek ayırma gibi olayları içerir.

 Bellek Yönetimi olarak sınıflandırılan blokların altında yatan nedenleri daha iyi anlamak için ilişkili çağrı yığınlarını ve profil raporlarını inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)