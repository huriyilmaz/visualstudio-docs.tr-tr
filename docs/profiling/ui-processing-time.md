---
title: UI Işlem zamanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63004462"
---
# <a name="ui-processing-time"></a>UI işlem süresi
Zaman çizelgesindeki bu segmentler, Kullanıcı arabirimi Işleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu, bir iş parçacığının Windows iletilerini balya da diğer kullanıcı arabirimi (UI) çalışmasını gerçekleştireceği anlamına gelir. Bu süre boyunca, concurrency Visualizer 'ın UI Işleme olarak sayan bir API 'de bir iş parçacığı engellenmiş. Ve gibi API `GetMessage()` 'ler `MsgWaitForMultipleObjects()` Bu gruba girer.

 Önceden tanımlı engelleme API 'SI tanımlanmazsa, gecikmenin temel nedenlerini öğrenmek için çağrı yığınlarını ve profil raporlarını gözden geçirin.

 Kullanıcı arabirimi Işleme kategorisi, GUI uygulamalarının yanıt hızını anlamanıza yardımcı olur ve UI yanıt verme süresini temel alan uygulamalarda tercih edilir. Örneğin, bir uygulamadaki UI iş parçacığı UI Işlemede %100 zaman alıyorsa, büyük olasılıkla yanıt verir. Ancak, UI iş parçacığı diğer kategorilerde önemli ölçüde zaman alıyorsa, kök nedenler ' i arayın ve bu iş parçacığında kullanıcı arabirimi olmayan kategorileri azaltma seçeneklerini göz önünde bulundurun.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)