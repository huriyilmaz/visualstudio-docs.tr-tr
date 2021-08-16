---
title: Boş Zaman Çizelgesi Segmenti | Microsoft Docs
description: Eşzamanlılık Visual Studio'nde, zaman çizelgesinin bir bölümünün bir tür kanal için boş (beyaz bir arka plana sahip) neden boş olduğunu anlıyoruz.
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
ms.openlocfilehash: 2bf348388f6668f2c3df5e439b28a5de58d5777df7e40e5b957ec824106af15f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427047"
---
# <a name="empty-timeline-segment"></a>Boş zaman çizelgesi kesimi
Eşzamanlılık Görselleştiricisi'nde zaman çizelgesinin bir bölümünün boş (beyaz bir arka plana sahip) neden olduğu kanal türüne bağlıdır.

- CPU iş parçacığı kanalı için iş parçacığının zaman çizelgesinin bu bölümünde var olmadığını gösterir. İş parçacığıyla ilgileniyorsanız, yakınlaştırma denetimi kullanarak veya yatay olarak kaydırarak yürütme bölümünü bulabilirsiniz.

- Bir I/O kanalı için, o zaman noktasında hedef işlem adına hiçbir disk erişimi meydana geldiği anlamına gelir.

- DirectX kanalı için, zaman çizelgesinin bu bölümünde hedef işlem adına GPU işi gerçekleştirilene anlamına gelir.

- İşaretçi kanalı için, hiçbir işaretçi oluşturulmadı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
- [Yakınlaştırma denetimi (İş Parçacıkları Görünümü)](../profiling/zoom-control-threads-view.md)