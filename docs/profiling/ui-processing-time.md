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
ms.openlocfilehash: cc852ee25e41c74f6153def656efcfe7185a66a5b02bdbbfd1c0eba2868d0ae3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270178"
---
# <a name="ui-processing-time"></a>UI işleme süresi
Zaman çizelgesinde yer alan bu segmentler, UI İşleme olarak kategorilere ayrılmış engelleme süreleri ile ilişkilendirilmektedir. Bu, bir iş parçacığının iletileri Windows veya diğer kullanıcı arabirimi (UI) çalışmalarını gerçekleştirerek olduğunu gösterir. Bu süre boyunca, Eşzamanlılık Görselleştiricisi'nin UI İşleme olarak sayıyor olduğu bir API'de bir iş parçacığı engellendi. ve gibi `GetMessage()` `MsgWaitForMultipleObjects()` API'ler bu gruba aittir.

 Önceden tanımlanmış bir engelleme API'si tanımlanmamışsa, gecikmenin temel nedenlerini belirlemek için çağrı yığınlarını ve profil raporlarını gözden geçirebilirsiniz.

 UI İşleme kategorisi GUI uygulamalarının yanıt hızını anlamanıza yardımcı olur ve kullanıcı arabirimi yanıt hızına bağlı uygulamalarda tercih edilir. Örneğin, bir uygulamanın kullanıcı arabirimi iş parçacığı UI İşleme'de %100 zaman elde ediyorsa, büyük olasılıkla yanıt verir. Ancak, kullanıcı arabirimi iş parçacığı diğer kategorilerde önemli ölçüde zaman harcanıyorsa, kök nedenlere bakın ve bu iş parçacığında kullanıcı arabirimi olmayan kategorileri azaltma seçeneklerini göz önünde bulundurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)