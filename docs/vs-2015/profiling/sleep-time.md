---
title: Uyku süresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198371"
---
# <a name="sleep-time"></a>Bekleme Süresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaman çizelgesindeki bu segmentler, uyku olarak sınıflandırılan engelleme süresi ile ilişkilendirilir. Uyku kategorisi, bir iş parçacığının kendi mantıksal çekirdeğini kendine vermiş olduğunu ve hiçbir iş olmadığını gösterir. Bu süre boyunca, eşzamanlılık görselleştiricinin uyku olarak saymakta olduğu bir API 'de bir iş parçacığı engellenmiştir. Ve gibi API `Sleep()` 'ler `SwitchToThread()` Bu gruba girer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
