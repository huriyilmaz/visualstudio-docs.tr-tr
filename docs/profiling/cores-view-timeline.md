---
title: Çekirdekler görünümü zaman çizelgesi | Microsoft Docs
description: 'Zaman çizelgesinin temellerini öğrenin: hangi iş parçacığının herhangi bir noktada hangi noktada çalıştığını ve nasıl yakınlaştırıp uzaklaşacağınızı belirleme.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882901"
---
# <a name="cores-view-timeline"></a>Çekirdekler görünümü zaman çizelgesi
Zaman çizelgesindeki her satır, profili oluşturulmuş sistemdeki mantıksal bir işlemci çekirdeğini temsil eder. Her satır için yatay eksen, belirli bir noktadaki mantıksal bir çekirdek üzerinde hangi iş parçacığının çalıştığını gösterir. İş parçacığını tanımlayan bir araç ipucunu döndürmek için bir zaman çizelgesinde ilgilendiğiniz bir rengin üzerine gelebilmeniz gerekir. İş parçacığı kimliği konusunda yardımcı olmak için pencerenin alt kısmındaki gösterge, her rengin ne temsil ettiğini gösterir. Yakınlaştırmak ve kapatmak için Yakınlaştır aracını kullanın ve CTRL tuşuna basarak veya fare tekerleğini taşıyarak yakınlaştırın. Çekirdek görünümü ve Iş parçacıkları görünümü arasında geçiş yaptığınızda yakınlaştırma tutarlılığı sürdürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [Çekirdekler Görünümü](../profiling/cores-view.md)
- [Yakınlaştırma denetimi (Iş parçacıkları görünümü)](../profiling/zoom-control-threads-view.md)