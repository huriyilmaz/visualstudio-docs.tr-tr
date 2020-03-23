---
title: Boş Zaman Çizelgesi Segmenti | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970115"
---
# <a name="empty-timeline-segment"></a>Boş zaman çizelgesi kesimi
Eşzamanlılık Görselleştiricisinde, zaman çizelgesinin bir bölümünün boş olmasının (beyaz bir arka plana sahip olmasının) nedeni kanalın türüne bağlıdır.

- CPU iş parçacığı kanalı için, iş parçacığı zaman çizelgesinin bu bölümünde var olmadığı anlamına gelir. İş parçacığıyla ilgileniyorsanız, yakınlaştırma denetimini kullanarak veya yatay kaydırma yaparak yürütme bölümünü bulabilirsiniz.

- Bir G/Ç kanalı için, o anda hedef işlem adına disk erişimi nin gerçekleşmemiş olduğu anlamına gelir.

- DirectX kanalı için, zaman çizelgesinin bu bölümünde hedef işlem adına GPU çalışması yapılmadığı anlamına gelir.

- Bir işaretleyici kanalı için, hiçbir işaretçi oluşturulduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
- [Yakınlaştırma denetimi (İş Parçacığı Görünümü)](../profiling/zoom-control-threads-view.md)