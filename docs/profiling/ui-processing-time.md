---
title: UI İşlem Süresi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "63004462"
---
# <a name="ui-processing-time"></a>UI işlem süresi
Zaman çizelgesindeki bu kesimler, UI Processing olarak kategorize edilen engelleme süreleri ile ilişkilidir. Bu, bir iş parçacığının Windows iletileri pompaladığını veya diğer kullanıcı arabirimi (UI) çalışmasını gerçekleştirdiği anlamına gelir. Bu süre zarfında, EşzamanlıLık Görselleştiricisi'nin UI İşleme olarak saydığı bir API'de bir iş parçacığı engellendi. API'ler `GetMessage()` `MsgWaitForMultipleObjects()` gibi ve bu gruba düşmek.

 Önceden tanımlanmış bir engelleme API'si tanımlanmamışsa, gecikmenin altında yatan nedenleri belirlemek için arama yığınlarını ve profil raporlarını gözden geçirin.

 Kullanıcı Arabirimi İşleme kategorisi GUI uygulamalarının yanıt verme yeteneğini anlamanıza yardımcı olur ve Kullanıcı Arabirimi yanıt verme durumuna bağlı uygulamalarda istenir. Örneğin, bir uygulamadaki Kullanıcı Arabirimi iş parçacığı Kullanıcı Arabirimi İşleminde %100 zaman elde ederse, büyük olasılıkla yanıt verir. Ancak, UI iş parçacığı diğer kategorilerde önemli ölçüde zaman harcıyorsa, kök nedenleri arayın ve bu iş parçacığı üzerinde UI olmayan kategorileri azaltmak için seçenekleri düşünün.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)