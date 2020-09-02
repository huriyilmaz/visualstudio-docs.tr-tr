---
title: GPU etkinlik grafiği | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969572"
---
# <a name="gpu-activity-graph"></a>GPU etkinlik grafiği
Eşzamanlılık görselleştiricisi içindeki GPU etkinlik grafiği, zaman içinde kullanımda olan DirectX altyapısının sayısıyla ölçülen, sistemdeki DirectX etkinliğinin düzeyini görüntüler.  Grafik hangi belirli altyapıların kullanıldığını göstermez.  Bir altyapının herhangi bir GPU işini işlemesi durumunda kullanımda olduğu kabul edilir.

## <a name="gpu-activity-graph-colors"></a>GPU etkinliği grafik renkleri
 Yeşil, geçerli işlem tarafından DirectX altyapısının tüketimini gösterir.

 Açık gri, DirectX altyapısının sistemdeki diğer işlemlere göre tüketimini gösterir. DirectX altyapısının diğer işlemlere göre kullanımını azaltmak için, sistemde çalışan diğer işlemlerin sayısını azaltın.

 Beyaz, sistemde kullanılmayan DirectX altyapılarının kullanılabilirliğini gösterir. Bunlardan faydalananlara daha fazla fırsat bulabiliyorsanız, bu altyapılarınız işleminiz için kullanılabilir. Bazı altyapılar yalnızca belirli türde görevler için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)