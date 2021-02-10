---
title: Uyku süresi | Microsoft Docs
description: Uyku kategorisinin bir iş parçacığının kendi mantıksal çekirdeğini sağladığını ve hiçbir iş olmadığını belirtir.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a433d11c2684a4a39660759f33d49bd719c2b2ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960175"
---
# <a name="sleep-time"></a>Uyku süresi
Zaman çizelgesindeki bu segmentler, uyku olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Uyku kategorisi, bir iş parçacığının kendi mantıksal çekirdeğini kendine vermiş olduğunu ve hiçbir iş olmadığını gösterir. Bu süre boyunca, eşzamanlılık görselleştiricinin uyku olarak saymakta olduğu bir API 'de bir iş parçacığı engellenmiştir. Ve gibi API `Sleep()` 'ler `SwitchToThread()` Bu gruba girer.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)