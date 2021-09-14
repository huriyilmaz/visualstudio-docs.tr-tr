---
title: Önk Zamanı | Microsoft Docs
description: Premption Time hakkında bilgi edinin ve zaman çizelgesinde yer alan bu segmentlerin Ön emption olarak kategorilere ayrılmış engelleme süresiyle ilişkili olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 02398447da41c1cb1442c7fb6a10b57625c2ecef
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628340"
---
# <a name="preemption-time"></a>Ön hazırlık süresi
Zaman çizelgesinde yer alan bu segmentler, Ön emption olarak kategorilere ayrılmış engelleme süresiyle ilişkilendirilmektedir. Bu kategori, bir iş parçacığının şu nedenlerden biri nedeniyle kapatıldığı anlamına gelir:

- Zamanlayıcı, daha yüksek öncelikli bir iş parçacığı kullanarak bunu değiştirdi.

- İş parçacığının yürütme kuantum süresi doldu ve diğer iş parçacıkları yürütülmaya hazırdı.

  Bu süre boyunca bir iş parçacığı, Eşzamanlılık Görselleştiricisi'nin Ön emption olarak sayma nedeniyle çekirdek bekleme nedeniyle engellendi. Ön emption segmentleri, bir iş parçacığı mantıksal çekirdekten çıkarılırken başlar ve bu iş parçacığı yürütmeyi sürdürürken sona erer.

  Önceden boşaltılan segmentin araç ipucu, ön emptiona neden olan işlem veya iş parçacığının adını görüntüler. Ancak bu, üzerine geçen sürecin veya iş parçacığının, önceki süre boyunca gerçekten çalışma yaptığına yönelik bir ifade değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)