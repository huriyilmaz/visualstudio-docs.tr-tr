---
title: Yürütme Süresi (İş Parçacıkları Görünümü) | Microsoft Docs
description: Eşzamanlılık Görselleştiricisinin İş Parçacıkları Görünümünde yürütme zamanlarını gözden geçirme. Yürütme süresi, bir iş parçacığının bir mantıksal çekirdekte etkin olarak ne zaman çalıştığını gösteren kesimler tarafından temsil edildi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 48455b4411994f61864a08aa05032bf8b0caafb3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131579"
---
# <a name="execution-time-threads-view"></a>Yürütme süresi (İş Parçacıkları Görünümü)
İş Parçacıkları Görünümü zaman çizelgesinde yer alan bu segmentler, iş parçacığı sistemde bir mantıksal çekirdek üzerinde etkin bir şekilde iş yaparken yürütme zamanlarını temsil eder.

 İş parçacığı durumundaki değişiklikler çekirdek bağlam anahtarı olayları aracılığıyla algılanır. Windows için Olay İzleme (ETW), her milisaniyede örnek yığınları yakalar. Çok kısa bir yeşil segmentte örnek alınmaz. Bu nedenle, bazı kısa yürütme segmentleri çağrı yığını göstermeyebilirsiniz.

 Bir yürütme segmentine tıklarken Eşzamanlılık Görselleştiricisi, tıklamanın bulunduğu konuma en yakın örnek yığını görüntüler. Bu örnek yığının konumu, zaman çizelgesinin üzerinde siyah bir ok veya giriş işaretiyle gösterilir ve örnek yığın Geçerli **sekmesinde** görünür.

 Geçerli görünümde tüm yürütme segmentleri için geleneksel örnekleme profilini görmek için Görünür Zaman Çizelgesi **Profili'nde** Yürütme'ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme Profil Raporu](../profiling/execution-profile-report.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)