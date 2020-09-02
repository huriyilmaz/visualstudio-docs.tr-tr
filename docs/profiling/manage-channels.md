---
title: Kanalları yönetme | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779248"
---
# <a name="manage-channels"></a>Kanalları Yönet
Eşzamanlılık görselleştiricisi içindeki **Iş parçacıkları görünümünde** , işlem için kanalları düzenleyerek belirli desenleri inceleyebilirsiniz. Kanalları sıralayabilir, yukarı ve aşağı taşıyabilir, gizleyebilir veya gösterebilirsiniz.

## <a name="sort-by"></a>Sıralama Ölçütü
 Geçerli yakınlaştırma düzeyine göre iş parçacıklarını farklı ölçütlere göre sıralamak için sıralama ölçütü denetimi kullanabilirsiniz. Bu, özellikle belirli bir model ararken yararlıdır. Şu ölçütlere göre sıralama yapabilirsiniz:

|Ölçütler|Tanım|
|--------------|----------------|
|Başlangıç Zamanı|İş parçacıklarını başlangıç sürelerine göre sıralar. Bu, varsayılan sıralama sıraladır.|
|Bitiş Zamanı|İş parçacıklarını bitiş sürelerine göre sıralar.|
|Yürütme|İş parçacıklarını yürütme sırasında harcanan sürenin yüzdesine göre sıralar.|
|Eşitleme|İş parçacıklarını eşitlemede harcanan sürenin yüzdesine göre sıralar.|
|G/Ç|İş parçacıklarını g/ç 'de harcanan sürenin yüzdesine göre sıralar (verileri okuma ve yazma).|
|Uyku|İş parçacıklarını, uyku modunda harcanan sürenin yüzdesine göre sıralar.|
|Sayfalama|İş parçacıklarını sayfalama sırasında harcanan sürenin yüzdesine göre sıralar.|
|Önalım|İş parçacıklarını önalım ' de harcanan sürenin yüzdesine göre sıralar.|
|UI Işleme|İş parçacıklarını Kullanıcı arabirimi işlemede harcanan sürenin yüzdesine göre sıralar.|

## <a name="move-selected-channel-up-or-down"></a>Seçili kanalı yukarı veya aşağı taşı
 Bu denetimleri listede bir kanalı yukarı veya aşağı taşımak için kullanabilirsiniz. Örneğin, belirli bir model veya bir çapraz iş parçacığı ilişkisini incelemenize yardımcı olması için birbirleriyle ilgili kanalları konumlandırabilirsiniz.

## <a name="move-selected-channel-to-top-or-bottom"></a>Seçili kanalı en üste veya en alta taşı
 Seçili kanalları listenin en üstüne veya altına taşıyarak belirli bir kalıbı inceleyebilir veya diğerlerini incelerken bazı kanalları izleyebilirsiniz.

## <a name="hide-selected-channels"></a>Seçili kanalları gizle
 Kanalları gizlemek istediğinizde bu denetimi seçin. Örneğin, bir iş parçacığı yönetilen işleminizin ömrü boyunca yüzde 100 Eşitleme ise, diğer iş parçacıklarını analiz ettiğiniz zaman onu gizleyebilirsiniz.

> [!NOTE]
> Bir iş parçacığının gizlenmesi, etkin göstergede ve profil raporlarında gösterilen hesaplama zamanından de kaldırılır.

## <a name="show-all-channels"></a>Tüm kanalları göster
 Bir veya daha fazla kanal gizliyse bu denetim etkin olur. Bunu seçerseniz, tüm gizli öğeler gösterilir ve zaman hesaplamalara döndürülür.

## <a name="move-markers-to-top"></a>İşaretçileri üste taşı
 Bir izleme işaret olaylarını içeriyorsa, işaretleyici kanalları zaman çizelgesinin en üstüne taşımak için bu komutu kullanabilirsiniz. Göreli sırası korunur.

## <a name="group-markers-by-thread"></a>İşaretçileri iş parçacığına göre grupla
 Bir izleme işaret olaylarını içeriyorsa, işaret olaylarını oluşturan iş parçacığının altında işaretleyici kanalları gruplandırmak için bu komutu kullanabilirsiniz.  Disk kanalları Kanal listesinin en üstüne taşınır ve GPU kanalları en alta taşınır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yakınlaştırma denetimi (Iş parçacıkları görünümü)](../profiling/zoom-control-threads-view.md)
- [Ölçü modu açık/kapalı](../profiling/measure-mode-on-off.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)