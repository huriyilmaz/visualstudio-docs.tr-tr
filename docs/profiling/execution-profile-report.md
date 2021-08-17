---
title: Yürütme Profili Raporu | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi uzantısında geleneksel örnekleme profili olan Yürütme Profili Raporu hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d62eac1bb37e297f9247241e4aac073e2406fdcc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061070"
---
# <a name="execution-profile-report"></a>Yürütme Profil Raporu
Yürütme Profili Raporu, geleneksel bir örnekleme profilidir. Örnekler, bir iş parçacığının mantıksal bir çekirdek üzerinde çalıştırılmış olduğu dönemlerde yaklaşık olarak her milisaniyede alınır ve Eşzamanlılık Görselleştiricisi, birikmiş örnek yığınları kümesi harmanlayarak tipik bir çağrı ağacını derlemeye devam eder. Bu tablodaki veriler geçerli zaman aralığından ve gizli iş parçacıklarında ve uygulanacak şu filtrelerden etkilenebilir:

- Seçili Yalnızca kendi kodum, yalnızca kullanıcı koduna sahip yığın çerçevelerinin yanı sıra kullanıcı kodunun bir düzeyi gösterilir.

- Gürültü azaltma değeri ayarlanırsa, belirtilen sıklıktan daha az olan harmanlama yığınları rapor dışında filtrelenmiş olur

  Aşağıdaki tabloda rapordaki sütunlar yer alır.

|Sütun|Açıklama|
|------------|-----------------|
|Ad|Çağrı yığınının her düzeyi için işlevin adı.|
|Kapsayıcı örnekler|Çağrı yığını ağacının bu düzeyine toplanan tüm yığınlar için toplanan toplam örnek sayısı. Kapsayıcı sayı, bu işlev için özel örneklerin ve tüm alt düğümleri için kapsayıcı sayaçların toplamıdır.|
|Özel Örnekler|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplam toplanan örnek sayısı.|
|% Kapsayıcı|Kapsayıcı örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanıyor.|
|Özel %|Özel örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanıyor.|
|Ayrıntılar|İşlevin tam adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

 Bu rapor tablosu Yürütme zamanı [(İş Parçacıkları Görünümü) görünümünde](../profiling/execution-time-threads-view.md) görülebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)