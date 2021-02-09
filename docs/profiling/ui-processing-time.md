---
title: UI Işlem zamanı | Microsoft Docs
description: Zaman çizelgesindeki segmentlerin, Kullanıcı arabirimi Işleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirildiğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809af327fc2bb608647a76575736bd0e2b00c5b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922030"
---
# <a name="ui-processing-time"></a>UI işlem süresi
Zaman çizelgesindeki bu segmentler, Kullanıcı arabirimi Işleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bu, bir iş parçacığının Windows iletilerini balya da diğer kullanıcı arabirimi (UI) çalışmasını gerçekleştireceği anlamına gelir. Bu süre boyunca, concurrency Visualizer 'ın UI Işleme olarak sayan bir API 'de bir iş parçacığı engellenmiş. Ve gibi API `GetMessage()` 'ler `MsgWaitForMultipleObjects()` Bu gruba girer.

 Önceden tanımlı engelleme API 'SI tanımlanmazsa, gecikmenin temel nedenlerini öğrenmek için çağrı yığınlarını ve profil raporlarını gözden geçirin.

 Kullanıcı arabirimi Işleme kategorisi, GUI uygulamalarının yanıt hızını anlamanıza yardımcı olur ve UI yanıt verme süresini temel alan uygulamalarda tercih edilir. Örneğin, bir uygulamadaki UI iş parçacığı UI Işlemede %100 zaman alıyorsa, büyük olasılıkla yanıt verir. Ancak, UI iş parçacığı diğer kategorilerde önemli ölçüde zaman alıyorsa, kök nedenler ' i arayın ve bu iş parçacığında kullanıcı arabirimi olmayan kategorileri azaltma seçeneklerini göz önünde bulundurun.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)