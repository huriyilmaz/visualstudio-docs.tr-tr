---
title: UI Işlem zamanı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145492"
---
# <a name="ui-processing-time"></a>UI İşleme Zamanı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaman çizelgesindeki bu segmentler, Kullanıcı arabirimi Işleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu, bir iş parçacığının Windows iletilerini balya da diğer kullanıcı arabirimi (UI) çalışmasını gerçekleştireceği anlamına gelir. Bu süre boyunca, concurrency Visualizer 'ın UI Işleme olarak sayan bir API 'de bir iş parçacığı engellenmiş. Ve gibi API `GetMessage()` 'ler `MsgWaitForMultipleObjects()` Bu gruba girer.  
  
 Önceden tanımlı engelleme API 'SI tanımlanmazsa, gecikmenin temel nedenlerini öğrenmek için çağrı yığınlarını ve profil raporlarını gözden geçirin.  
  
 Kullanıcı arabirimi Işleme kategorisi, GUI uygulamalarının yanıt hızını anlamak için önemlidir ve UI yanıt verme süresini temel alan uygulamalarda tercih edilir. Örneğin, bir uygulamadaki UI iş parçacığı UI Işlemede %100 defa elde alıyorsa, büyük olasılıkla çok yanıt verir. Ancak, UI iş parçacığı diğer kategorilerde önemli ölçüde zaman alıyorsa, kök nedenler ' i arayın ve bu iş parçacığında kullanıcı arabirimi olmayan kategorileri azaltma seçeneklerini göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
