---
title: GPU Etkinlik Grafiği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5734b9eb1b4307f7c32dcb8a170f7c6c571f46ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969572"
---
# <a name="gpu-activity-graph"></a>GPU Etkinlik grafiği
EşzamanlıLık Görselleştiricisindeki GPU Etkinlik grafiği, zaman içinde kullanılmakta olan DirectX motorsayısıyla ölçülen sistemdeki DirectX etkinlik düzeyini görüntüler.  Grafik, hangi belirli motorların kullanıldığını göstermez.  Herhangi bir GPU çalışmasını işliyorsa, bir motorun kullanımda olduğu kabul edilir.

## <a name="gpu-activity-graph-colors"></a>GPU Etkinlik grafik renkleri
 Yeşil, DirectX Motorlarının geçerli işlemle tüketimini gösterir.

 Açık gri, DirectX Motorlarının sistemdeki diğer işlemler tarafından tüketimini gösterir. DirectX motorlarının tüketimini diğer işlemlere göre azaltmak için, sistemde çalışan diğer işlemlerin sayısını azaltın.

 Beyaz, kullanılmayan DirectX motorlarının sistemdeki kullanılabilirliğini gösterir. Eğer onları yararlanmak için daha fazla fırsat bulabilirseniz bu motorlar süreciiçin kullanılabilir. Bazı motorlar yalnızca belirli türde görevler için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)