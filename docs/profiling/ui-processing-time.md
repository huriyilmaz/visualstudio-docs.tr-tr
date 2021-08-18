---
title: UI İşleme Süresi | Microsoft Docs
description: Zaman çizelgesinde segmentlerin UI İşleme olarak kategorilere ayrılmış engelleme zamanları ile ilişkili olduğunu öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 160200ebb40f99ce2f22086d5904995cc54e9a80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141057"
---
# <a name="ui-processing-time"></a>UI işleme süresi
Zaman çizelgesinde yer alan bu segmentler, UI İşleme olarak kategorilere ayrılmış engelleme süreleri ile ilişkilendirilmektedir. Bu, bir iş parçacığının iletileri Windows veya diğer kullanıcı arabirimi (UI) çalışmalarını gerçekleştirerek olduğunu gösterir. Bu süre boyunca, Eşzamanlılık Görselleştiricisi'nin UI İşleme olarak sayıyor olduğu bir API'de iş parçacığı engellendi. ve gibi `GetMessage()` `MsgWaitForMultipleObjects()` API'ler bu gruba aittir.

 Önceden tanımlanmış bir engelleme API'si tanımlanmamışsa, gecikmenin temel nedenlerini belirlemek için çağrı yığınlarını ve profil raporlarını gözden geçirebilirsiniz.

 UI İşleme kategorisi GUI uygulamalarının yanıt hızını anlamanıza yardımcı olur ve kullanıcı arabirimi yanıt hızına bağlı uygulamalarda tercih edilir. Örneğin, bir uygulamanın kullanıcı arabirimi iş parçacığı UI İşleme'de %100 zaman elde ediyorsa, büyük olasılıkla yanıt verir. Ancak, kullanıcı arabirimi iş parçacığı diğer kategorilerde önemli ölçüde zaman harcanıyorsa, kök nedenlere bakın ve bu iş parçacığında UI olmayan kategorileri azaltma seçeneklerini göz önünde bulundurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)