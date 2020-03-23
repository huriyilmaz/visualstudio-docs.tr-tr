---
title: Kanalları Yönetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1480bab2f52383a8ca3a5b0ac22fd56acb5e01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "64779248"
---
# <a name="manage-channels"></a>Kanalları Yönet
Eşzamanlılık Görselleştiricisindeki **İş Parçacıkları Görünümü'nde,** belirli desenleri inceleyebilmeniz için işleminiz için kanalları düzenleyebilirsiniz. Kanalları sıralayabilir, yukarı ve aşağı taşıyabilir ve saklayabilir veya gösterebilirsiniz.

## <a name="sort-by"></a>Sıralama Ölçütü
 İş parçacıklarını geçerli yakınlaştırma düzeyine göre farklı ölçütlere göre sıralamak için Sırala denetimini kullanabilirsiniz. Belirli bir desen arıyorsanız bu özellikle yararlıdır. Şu ölçütleri sıralayabilirsiniz:

|Ölçütler|Tanım|
|--------------|----------------|
|Başlangıç Zamanı|İş parçacıklarını başlangıç saatlerine göre sıralar. Bu varsayılan sıralama sırasıdır.|
|Bitiş Zamanı|İş parçacıklarını bitiş saatlerine göre sıralar.|
|Yürütme|İş parçacıklarını yürütmede harcanan süreye göre sıralar.|
|Eşitleme|İş parçacıklarını eşitlemede harcanan zaman yüzdelerine göre sıralar.|
|G/Ç|İş parçacıklarını G/Ç'de (verileri okuma ve yazma) harcanan zaman yüzdelerine göre sıralar.|
|Uyku|İş parçacıklarını uykuda harcanan süreye göre sıralar.|
|Sayfalama|İş parçacıklarını sayfalama da harcanan zaman yüzdelerine göre sıralar.|
|Preemption|İş parçacıklarını, preemption'da harcanan zaman yüzdelerine göre sıralar.|
|UI İşleme|İş parçacıklarını, kullanıcı arabirimi işlemede harcanan süreye göre sıralar.|

## <a name="move-selected-channel-up-or-down"></a>Seçili kanalı yukarı veya aşağı taşıma
 Bir kanalı listede yukarı veya aşağı taşımak için bu denetimleri kullanabilirsiniz. Örneğin, belirli bir deseni veya iş parçacığı ilişkisini incelemenize yardımcı olmak için ilgili kanalları yan yana konumlandırabilirsiniz.

## <a name="move-selected-channel-to-top-or-bottom"></a>Seçili kanalı üst veya alta taşıma
 Belirli bir deseni inceleyebilmek için seçili kanalları listenin en üstüne veya altına taşıyabilir veya bazı kanalları diğerlerini incelerken yoldan çekebilirsiniz.

## <a name="hide-selected-channels"></a>Seçili kanalları gizleme
 Kanalları gizlemek istediğinizde bu denetimi seçin. Örneğin, bir iş parçacığı yönetilen işlemin ömrü için yüzde 100 eşitleme ise, diğer iş parçacığı çözümlemek gibi gizleyebilirsiniz.

> [!NOTE]
> İş parçacığı gizleme, etkin göstergede ve profil raporlarında gösterilen hesaplama saatinden de kaldırır.

## <a name="show-all-channels"></a>Tüm kanalları göster
 Bir veya daha fazla kanal gizlendiğinde bu denetim etkindir. Bunu seçerseniz, tüm gizli öğeler gösterilir ve zaman hesaplamalarına döndürülür.

## <a name="move-markers-to-top"></a>İşaretçileri en üste taşıma
 Bir izleme işaretleyici olayları içeriyorsa, işaretçi kanallarını zaman çizelgesinin en üstüne taşımak için bu komutu kullanabilirsiniz. Göreceli düzenleri korunur.

## <a name="group-markers-by-thread"></a>İş parçacığına göre grup işaretleri
 Bir izleme işaretçi olayları içeriyorsa, işaretçi olaylarını oluşturan iş parçacığının altında işaretçilerkanallarını gruplandırmak için bu komutu kullanabilirsiniz.  Disk kanalları kanal listesinin en üstüne, GPU kanalları ise en alta taşınır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yakınlaştırma denetimi (İş Parçacığı Görünümü)](../profiling/zoom-control-threads-view.md)
- [Ölçme modu a/kapalı](../profiling/measure-mode-on-off.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)