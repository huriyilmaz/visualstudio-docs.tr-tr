---
title: Uyku Süresi | Microsoft Docs
description: Uyku kategorisinin, bir iş parçacığının kendi mantıksal çekirdeğini gönüllü olarak verdiğine ve hiçbir iş yaptığına ima ettiğini öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1b1ddc13733f9613ee168b1e4a218ec4f08f0d10
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141590"
---
# <a name="sleep-time"></a>Uyku süresi
Zaman çizelgesinde yer alan bu segmentler, Uyku olarak kategorilere ayrılmış engelleme süresiyle ilişkilendirilmektedir. Uyku kategorisi, bir iş parçacığının mantıksal çekirdeğini isteğe bağlı olarak verdiği ve hiçbir iş yaptığı anlamına gelir. Bu süre boyunca, Eşzamanlılık Görselleştiricisi'nin Uyku olarak sayıyor olduğu bir API'de iş parçacığı engellendi. ve gibi `Sleep()` `SwitchToThread()` API'ler bu gruba aittir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)