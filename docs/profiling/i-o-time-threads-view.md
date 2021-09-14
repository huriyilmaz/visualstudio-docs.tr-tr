---
title: G-ç zamanı (Iş parçacıkları görünümü) | Microsoft Docs
description: G/ç olarak kategorilere ayrılan engelleme süreleriyle ilgili olarak g/ç zaman segmentlerinin nasıl ilişkilendirildiğini öğrenin. Bu, bir iş parçacığının g/ç işleminin bitmesini beklediği anlamına gelir.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 527ab5a69de0698ac876adf2e7b75d540e7e51a3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635681"
---
# <a name="io-time-threads-view"></a>G/Ç zamanı (İş Parçacıkları Görünümü)
Zaman çizelgesindeki bu segmentler, g/ç olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu, bir iş parçacığının bir g/ç işleminin bitmesini beklediği anlamına gelir. İş parçacığı bir API 'de engellenmiş olabilir veya g/ç ile ilgili bir çekirdek, eşzamanlılık görselleştiricinin g/ç olarak sayımının tamamlanmasını bekler. , Ve gibi API 'Ler `CreateFile()` `ReadFile()` `WSARecv()` Bu gruba girer.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)