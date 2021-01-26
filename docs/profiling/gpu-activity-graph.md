---
title: GPU etkinlik grafiği | Microsoft Docs
description: Sistemdeki DirectX etkinliğinin düzeyinde bulunan eşzamanlılık görselleştiricisi içinde görüntülenen GPU etkinlik grafiğini anlayın.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bccf4869a1197306017b443b00670cc123300a48
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801323"
---
# <a name="gpu-activity-graph"></a>GPU etkinlik grafiği
Eşzamanlılık görselleştiricisi içindeki GPU etkinlik grafiği, zaman içinde kullanımda olan DirectX altyapısının sayısıyla ölçülen, sistemdeki DirectX etkinliğinin düzeyini görüntüler.  Grafik hangi belirli altyapıların kullanıldığını göstermez.  Bir altyapının herhangi bir GPU işini işlemesi durumunda kullanımda olduğu kabul edilir.

## <a name="gpu-activity-graph-colors"></a>GPU etkinliği grafik renkleri
 Yeşil, geçerli işlem tarafından DirectX altyapısının tüketimini gösterir.

 Açık gri, DirectX altyapısının sistemdeki diğer işlemlere göre tüketimini gösterir. DirectX altyapısının diğer işlemlere göre kullanımını azaltmak için, sistemde çalışan diğer işlemlerin sayısını azaltın.

 Beyaz, sistemde kullanılmayan DirectX altyapılarının kullanılabilirliğini gösterir. Bunlardan faydalananlara daha fazla fırsat bulabiliyorsanız, bu altyapılarınız işleminiz için kullanılabilir. Bazı altyapılar yalnızca belirli türde görevler için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)