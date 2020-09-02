---
title: G-ç zamanı (Iş parçacıkları görünümü) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62995448"
---
# <a name="io-time-threads-view"></a>G/Ç zamanı (İş Parçacıkları Görünümü)
Zaman çizelgesindeki bu segmentler, g/ç olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu, bir iş parçacığının bir g/ç işleminin bitmesini beklediği anlamına gelir. İş parçacığı bir API 'de engellenmiş olabilir veya g/ç ile ilgili bir çekirdek, eşzamanlılık görselleştiricinin g/ç olarak sayımının tamamlanmasını bekler. , Ve gibi API 'Ler `CreateFile()` `ReadFile()` `WSARecv()` Bu gruba girer.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)