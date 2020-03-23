---
title: I-O Saati (İş Parçacığı Görünümü) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62995448"
---
# <a name="io-time-threads-view"></a>G/Ç zamanı (İş Parçacıkları Görünümü)
Zaman çizelgesindeki bu segmentler, G/Ç olarak kategorize edilen engelleme süreleri ile ilişkilidir. Bu, bir iş parçacığının Bir G/Ç işleminin tamamlanmasını beklediği anlamına gelir. İş parçacığı bir API'de veya EşzamanlıLık Görselleştiricisinin G/Ç olarak saydığı G/Ç ile ilgili bir çekirdek beklemesi ile engellenmiş olabilir. API'ler `CreateFile()` `ReadFile()`gibi `WSARecv()` , , ve bu gruba düşmek.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)