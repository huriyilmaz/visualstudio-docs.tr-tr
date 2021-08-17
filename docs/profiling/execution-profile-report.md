---
title: Yürütme profili raporu | Microsoft Docs
description: Visual Studio için eşzamanlılık görselleştiricisi uzantısında geleneksel bir örnekleme profili olan yürütme profili raporu hakkında bilgi edinin.
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
ms.openlocfilehash: 3e08c84437bc8b24b0e7bd16d11bbe7bdee3852753ad93f2b4f84a32b7377585
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396662"
---
# <a name="execution-profile-report"></a>Yürütme Profil Raporu
Yürütme profili raporu, geleneksel bir örnekleme profilidir. Örnekler, bir iş parçacığı mantıksal bir çekirdek üzerinde çalışırken, zaman aralığı boyunca yaklaşık olarak her milisaniyeye alınır ve eşzamanlılık görselleştiricisi, örnek yığınları birikmiş kümesini harmanlayarak tipik bir çağrı ağacı oluşturur. Bu tablodaki veriler geçerli zaman aralığı ve gizli iş parçacıklarından ve uygulanabilecek Bu filtrelerle etkilenebilir:

- Yalnızca kendi kodum seçilirse yalnızca Kullanıcı kodu olan ve kullanıcı kodunun altında bir düzey olan yığın çerçeveleri gösterilir.

- Gürültü azaltma değeri ayarlandıysa, belirtilen sıklığından daha az olan harmanlanmış yığınlar raporun dışına filtrelenir

  Aşağıdaki tabloda rapordaki sütunlar gösterilmektedir.

|Sütun|Açıklama|
|------------|-----------------|
|Ad|Çağrı yığınının her bir düzeyi için işlevin adı.|
|Kapsamlı örnekler|Çağrı yığını ağacının bu düzeyine toplanan tüm yığınlar için toplanan örneklerin toplam sayısı. Dahil edilen sayı, bu işlev için dışlamalı örneklerin toplamı ve tüm alt düğümleri için kapsamlı sayaçlardır.|
|Dışlamalı örnekler|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplam toplanan örnek sayısı.|
|Dahil yüzdesi|Kapsamlı örnekler sütununda gösterilen toplam örnek yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanır.|
|% Özel|Dışlamalı örnekler sütununda gösterilen toplam örnek yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanır.|
|Ayrıntılar|İşlevin tam adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

 Bu rapor tablosu, [yürütme zamanı (Iş parçacıkları görünümü)](../profiling/execution-time-threads-view.md) görünümünde görülebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)