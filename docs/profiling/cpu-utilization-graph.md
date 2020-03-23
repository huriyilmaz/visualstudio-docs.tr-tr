---
title: CPU Kullanım Grafiği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e09526930bf98141ae4f9d4d204b20383763c208
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552882"
---
# <a name="cpu-utilization-graph"></a>CPU Kullanım grafiği
CPU Kullanım grafiği, zaman içinde bir uygulamadaki kullanım düzeyini gösterir. X ekseni izleme süresini, y ekseni ise sistemdeki mantıksal çekirdek sayısını temsil eder. Grafik, belirli bir anda hangi çekirdeğin etkin olduğunu göstermez. Örneğin, iki çekirdeğin her biri belirli bir süre için yüzde 50 kapasiteyle çalışıyorsa, bu görünüm kullanılan bir mantıksal çekirdeği gösterir.

## <a name="cpu-utilization-graph-colors"></a>CPU Kullanım grafiği renkleri

- Yeşil, sistemdeki mantıksal çekirdeklerin geçerli işlem tarafından kullanılmasını gösterir.

- Açık gri, mantıksal çekirdeklerin sistemdeki diğer işlemler tarafından kullanılmasını gösterir. CPU grafiğindeki yüksek yüzdelik açık gri, sistemin diğer işlemler tarafından yoğun şekilde yüklendiğini ve işleminizin onlar tarafından önceden boşaltılmış olabileceğini gösterir. Mantıksal çekirdeklerin diğer işlemlertarafından tüketimini azaltmak için, sistemde çalışan çekirdek sayısını azaltın.

- Koyu gri, mantıksal çekirdeklerin sistem işlemine göre tüketimini gösterir. Bunu doğrudan denetleyemezsiniz, ancak işleminiz için mantıksal çekirdeklerin kullanılabilirliğini etkileyebileceğinden, ne zaman oluştuğunu bilmek yararlıdır.

- Beyaz, sistemde kullanılmayan mantıksal çekirdeklerin kullanılabilirliğini gösterir. Eğer paralellik için daha fazla fırsat bulabilirseniz bu çekirdekler süreciniz için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)
- [Ortalama CPU Kullanımı](../profiling/average-cpu-utilization.md)