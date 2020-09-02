---
title: Uyku süresi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980219"
---
# <a name="sleep-time"></a>Uyku süresi
Zaman çizelgesindeki bu segmentler, uyku olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Uyku kategorisi, bir iş parçacığının kendi mantıksal çekirdeğini kendine vermiş olduğunu ve hiçbir iş olmadığını gösterir. Bu süre boyunca, eşzamanlılık görselleştiricinin uyku olarak saymakta olduğu bir API 'de bir iş parçacığı engellenmiştir. Ve gibi API `Sleep()` 'ler `SwitchToThread()` Bu gruba girer.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)