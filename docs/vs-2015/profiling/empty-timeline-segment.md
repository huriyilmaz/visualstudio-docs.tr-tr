---
title: Boş zaman çizelgesi segmenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0291cfe93492c357401ce371d58683c6815aa12b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179042"
---
# <a name="empty-timeline-segment"></a>Boş Zaman Çizelgesi Segmenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi içinde, zaman çizelgesinin bir bölümünün boş olması neden olur (beyaz bir arka plana sahiptir) Kanal türüne bağlıdır.  
  
- Bir CPU iş parçacığı kanalı için, iş parçacığının bu bölümü zaman çizelgesinin bu kısmı sırasında olmadığı anlamına gelir. İş parçacığı ile ilgileniyorsanız, Yakınlaştırma denetimini kullanarak veya yatay olarak kaydırma yaparak yürütülmekte olan bölümünü bulabilirsiniz.  
  
- G/ç kanalı için, bu noktada hedef işlem adına disk erişimi gerçekleşmediği anlamına gelir.  
  
- DirectX kanalı için, zaman çizelgesinin bu bölümü sırasında hedef işlem adına hiçbir GPU işi gerçekleştirilmediği anlamına gelir.  
  
- İşaretleyici kanal için, hiçbir işaretleyici üretilmediği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)   
 [Yakınlaştırma Denetimi (İş Parçacıkları Görünümü)](../profiling/zoom-control-threads-view.md)
