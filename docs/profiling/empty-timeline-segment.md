---
title: Boş zaman çizelgesi segmenti | Microsoft Docs
description: Visual Studio eşzamanlılık görselleştiricisi içinde, bir kanal türü için bir zaman çizelgesinin bir bölümünün boş (beyaz bir arka plana sahip) olma nedenini anlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 367d82905e46eeacd9bb20c9e8a7444ce804ffe2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150410"
---
# <a name="empty-timeline-segment"></a>Boş zaman çizelgesi segmenti
Eşzamanlılık görselleştiricisi içinde, zaman çizelgesinin bir bölümünün boş olması neden olur (beyaz bir arka plana sahiptir) Kanal türüne bağlıdır.

- Bir CPU iş parçacığı kanalı için, iş parçacığının bu bölümü zaman çizelgesinin bu kısmı sırasında olmadığı anlamına gelir. İş parçacığı ile ilgileniyorsanız, Yakınlaştırma denetimini kullanarak veya yatay olarak kaydırma yaparak yürütülmekte olan bölümünü bulabilirsiniz.

- G/ç kanalı için, bu noktada hedef işlem adına disk erişimi gerçekleşmediği anlamına gelir.

- DirectX kanalı için, zaman çizelgesinin bu bölümü sırasında hedef işlem adına hiçbir GPU işi gerçekleştirilmediği anlamına gelir.

- İşaretleyici kanal için, hiçbir işaretleyici üretilmediği anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
- [Yakınlaştırma denetimi (Iş parçacıkları görünümü)](../profiling/zoom-control-threads-view.md)