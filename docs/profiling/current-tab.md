---
title: Geçerli sekme | Microsoft Docs
description: CPU iş parçacığı segmentinin veya engelleme segmentinin çağrı yığınını görmek için Iş parçacıkları görünümünün geçerli sekmesini seçin. DirectX kesimleri hakkında da bilgi de mevcuttur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65261d6304ead5ade7c28f40495fa68afb0c2171
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686226"
---
# <a name="current-tab"></a>Geçerli sekme
**Geçerli** sekmeye tıklayarak, bir CPU iş parçacığı kesimi seçildiyse, zaman çizelgesinde geçerli seçim noktasına en yakın olan çağrı yığınını (varsa) görebilirsiniz.  Bu durumda seçim noktası, zaman çizelgesinin üzerindeki bir siyah ok veya şapka ile temsil edilir. Engelleyici bir segment seçildiğinde, bir yürütme olmadığından giriş işareti görüntülenmez. Ancak, segment hala vurgulanmıştır ve bir çağrı yığını görüntülenir.

 **Geçerli** sekme, DirectX etkinlik kesimleri, işaretleyiciler ve g/ç erişimiyle ilgili bilgileri de görüntüler.  DirectX etkinlik kesimleri için, DMA paketlerinin donanım kuyruğu tarafından işlenme şekli hakkında bilgi görüntülenir.  İşaretleyiciler için, açıklama ve işaret türü hakkında bilgi görüntülenir.  G/ç erişimi için, dosya ve okunan veya yazılan bayt sayısı hakkında bilgi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)