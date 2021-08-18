---
title: Kanalları Yönetme | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nde İş Parçacıkları Görünümü'nde belirli desenleri inceleyecek şekilde sürecinizin kanallarını nasıl düzenleyebilirsiniz?
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 225d261cad0e4e8c206c00e124478a83e2710845
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131293"
---
# <a name="manage-channels"></a>Kanalları Yönet
Eşzamanlılık  Görselleştiricisi'nde İş Parçacıkları Görünümü'nde, belirli desenleri inceleyecek şekilde işleminizin kanallarını düzenleyebilirsiniz. Kanalları sıralar, yukarı ve aşağı hareket ettirin ve gizleyebilirsiniz veya gösterebilirsiniz.

## <a name="sort-by"></a>Sıralama Ölçütü
 İş parçacıklarını geçerli yakınlaştırma düzeyine göre farklı ölçütlere göre sıralamak için Sıralama Ölçütü denetimi kullanabilirsiniz. Bu özellikle belirli bir deseni arıyorken yararlıdır. Şu ölçütlere göre sıraabilirsiniz:

|Ölçütler|Tanım|
|--------------|----------------|
|Başlangıç Zamanı|İş parçacıklarını başlangıç zamanlarına göre sıralar. Bu, varsayılan sıralama düzenidir.|
|Bitiş Zamanı|İş parçacıklarını bitiş zamanlarına göre sıralar.|
|Yürütme|İş parçacıklarını yürütmede harcanan süre yüzdesine göre sıralar.|
|Eşitleme|İş parçacıklarını eşitlemede harcanan süre yüzdesine göre sıralar.|
|G/Ç|İş parçacıklarını, I/O'da harcanan sürenin yüzdesine (veri okuma ve yazma) göre sıralar.|
|Uyku|İş parçacıklarını uykuda harcanan süre yüzdesine göre sıralar.|
|Sayfalama|İş parçacıklarını disk belleğine harcanan süre yüzdesine göre sıralar.|
|Ön önklere çıkma|İş parçacıklarını ön hazırlık için harcanan süre yüzdesine göre sıralar.|
|UI İşleme|İş parçacıklarını kullanıcı arabirimi işlemeye harcanan süre yüzdesine göre sıralar.|

## <a name="move-selected-channel-up-or-down"></a>Seçili kanalı yukarı veya aşağı taşıma
 Bir kanalı listede yukarı veya aşağı taşımak için bu denetimleri kullanabilirsiniz. Örneğin, belirli bir deseni veya bir iş parçacığı çapraz ilişkisini incelemeye yardımcı olmak için ilgili kanalları yan yan konuma getirin.

## <a name="move-selected-channel-to-top-or-bottom"></a>Seçili kanalı üst veya alta taşıma
 Belirli bir düzeni incelemek veya bazı kanalları incelerken bazı kanalların yolunun dışında hareket etmek için, seçilen kanalları listenin en üstüne veya altına taşıyabilirsiniz.

## <a name="hide-selected-channels"></a>Seçili kanalları gizleme
 Kanalları gizlemek istediğiniz zaman bu denetimi seçin. Örneğin, bir iş parçacığı yönetilen işleminizin ömrü boyunca yüzde 100 eşitleme ise, diğer iş parçacıklarını analiz ederken iş parçacığını gizleyebilirsiniz.

> [!NOTE]
> Bir iş parçacığını gizleme işlemi, etkin göstergede ve profil raporlarında gösterilen hesaplama zamanından da kaldırır.

## <a name="show-all-channels"></a>Tüm kanalları göster
 Bir veya daha fazla kanal gizli olduğunda bu denetim etkindir. Bunu seçerseniz tüm gizli öğeler gösterilir ve zaman hesaplamalarına döndürülür.

## <a name="move-markers-to-top"></a>İşaretçileri yukarı taşıma
 İzleme işaretçi olayları içeriyorsa, işaretçi kanallarını zaman çizelgesinin en üstüne taşımak için bu komutu kullanabilirsiniz. Göreli sıraları korunur.

## <a name="group-markers-by-thread"></a>İşaretçileri iş parçacığına göre grupla
 Bir izleme işaretçi olayları içeriyorsa, işaretçi olaylarını oluşturan iş parçacığı altında işaretçi kanallarını grup oluşturmak için bu komutu kullanabilirsiniz.  Disk kanalları kanal listesinin en üstüne, GPU kanalları ise en alta taşınır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yakınlaştırma denetimi (İş Parçacıkları Görünümü)](../profiling/zoom-control-threads-view.md)
- [Ölçü modu kapalı/kapalı](../profiling/measure-mode-on-off.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)