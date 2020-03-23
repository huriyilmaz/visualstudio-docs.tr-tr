---
title: Yürütme Profili Raporu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25886ad4f7c31ea02c8dab2d45d8709a362a5a69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969998"
---
# <a name="execution-profile-report"></a>Yürütme Profil Raporu
Yürütme Profil Raporu geleneksel bir örnekleme profilidir. Örnekler, bir iş parçacığının mantıksal bir çekirdek üzerinde çalışırken olduğu dönemlerde yaklaşık her milisaniyede bir alınır ve Eşzamanlılık Görselleştiricisi, birikmiş örnek yığınları kümesini harmanlayarak tipik bir çağrı ağacı oluşturur. Bu tablodaki veriler geçerli zaman aralığı ve gizli iş parçacıkları ve uygulanabilecek bu filtreler den etkilenebilir:

- Yalnızca Kodum seçilirse, yalnızca kullanıcı koduna sahip yığın çerçeveleri ve kullanıcı kodunun altında bir düzey gösterilir.

- Gürültü azaltma değeri ayarlanırsa, belirtilen frekanstan daha az olan harmanlanmış yığınlar rapordan filtrelenir

  Aşağıdaki tabloda raporda sütunlar gösterilmektedir.

|Sütun|Açıklama|
|------------|-----------------|
|Adı|Çağrı yığınının her düzeyi için işlevin adı.|
|Dahil numuneler|Çağrı yığını ağacının bu düzeyine yuvarlanan tüm yığınlar için toplanan toplam örnek sayısı. Kapsayıcı sayı, bu işlev için özel örneklerin ve tüm alt düğümleri için kapsayıcı sayaçların toplamıdır.|
|Özel Örnekler|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplanan örneklerin toplam sayısı.|
|% Dahil|Kapsayıcı örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzdeler iki ondalık basamak lara yuvarlanır.|
|% Özel|Özel örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzdeler iki ondalık basamak lara yuvarlanır.|
|Ayrıntılar|Fonksiyonun tam nitelikli adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

 Bu rapor tablosu Yürütme [süresi (İş Parçacıkları Görünümü)](../profiling/execution-time-threads-view.md) görünümünde görülebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)