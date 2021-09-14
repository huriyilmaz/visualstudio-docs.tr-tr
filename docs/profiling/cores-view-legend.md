---
title: Çekirdekler görünümü göstergesi | Microsoft Docs
description: Tablo bağlamı anahtar verileri ve iş parçacığı seçimi sağlayan çekirdek görünümü göstergesi hakkında bilgi edinin. Ayrıca bağlam geçişleri ve performansı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 21d753fdcd1076a79cb2fcde8698430cb5de31e5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725704"
---
# <a name="cores-view-legend"></a>Çekirdekler görünümü göstergesi
Çekirdekler görünümü göstergesi her bir iş parçacığını renge ve ada göre tanımlar. Bu, platformlar arası bağlam anahtarları, toplam bağlam geçişleri ve çekirdekler arası bağlam anahtarlarının yüzdesi gösteren sütunları içerir. Göstergedeki satırlar, azalan sırada çapraz çekirdek bağlam anahtarları sayısına göre sıralanır.

 Zaman çizelgesinde görüntülenen iş parçacıklarını filtrelemek için göstergedeki satırları seçebilirsiniz. Yalnızca seçilen iş parçacıkları zaman çizelgesinde gösterilir. Hiçbir satır seçilmezse, tüm satırlar zaman çizelgesinde gösterilir.

 Platformlar arası bağlam geçişleri, aynı mantıksal çekirdek üzerinde kalan anahtarlardan daha fazla ek yük ve performans maliyeti getirir. Bağlam anahtarları sırasında, işlemci kayıtları kaydedilir ve geri yüklenir, işletim sistemi çekirdek kodu yürütülür, çeviri arabelleği arabellek girdileri yeniden yüklenir ve işlemci işlem hattı temizlenir. Diğer bir çekirdek üzerinde bu iş parçacığı için önbellek verileri geçerli olmadığından, platformlar arası bağlam geçişleri diğer bağlam anahtarlarından daha pahalı olabilir. Buna karşılık, bir iş parçacığı daha önce üzerinde çalıştığı temel üzerine geçiş yapmışsa, faydalı verilerin hala önbellekte olması olasıdır. Platformlar arası bağlam geçişleri, iş parçacığı benzeşimini yönetme girişimleri tarafından arttırılırsa ve performans düşer ise, bu sorunu ele almak isteyip istemediğinizi göz önünde bulundurun. İş parçacığı benzeşimini ortadan kaldırarak başlayın ve ardından ortaya çıkan çekirdek davranışını gözlemleyin.

 Aşağıdaki tabloda gösterge öğeleri açıklanmaktadır.

|Öğe|Tanım|
|-------------|----------------|
|İş parçacığı adı|Önceki çekirdekler zaman çizelgesinde iş parçacığının rengini ve bu iş parçacığının adını gösterir.|
|Platformlar arası bağlam geçişleri|Aynı zamanda bir mantıksal çekirdekden diğerine geçiş yapan bir iş parçacığının bağlam anahtarı sayısı. Bu, bir işlemciden diğerine kadar olan platformlar arası bağlam anahtarları arasında ayrım yapmaz.|
|Toplam bağlam geçişi|Örnekleme döneminde belirli bir iş parçacığı için bağlam anahtarlarının toplam sayısı. Bir iş parçacığının bağlamı her değiştirdiğinde (örneğin, yürütmenin eşitlemesine) bir bağlam anahtarı sayılır.|
|Çekirdekler arası bağlam anahtarlarının yüzdesi|Çapraz çekirdek bağlam anahtarlarının sayısı toplam bağlam anahtarı sayısına bölünerek yüzde olarak hesaplanır. Bu yüzdenin ne kadar yüksekse, bu belirli iş parçacığının performansı üzerinde, platformlar arası bağlam geçişlerinin genel etkisinin ne kadar yüksek olması gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çekirdekler Görünümü](../profiling/cores-view.md)