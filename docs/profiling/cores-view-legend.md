---
title: Cores View Legend | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea3184fbcd3561b88521f7dbdf4bf44c925150d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553169"
---
# <a name="cores-view-legend"></a>Cores View efsanesi
Cores View göstergesi her iş parçacığını renk ve ada göre tanımlar. Çekirdekler arası bağlam anahtarları, toplam bağlam anahtarları ve çekirdekleri geçen bağlam anahtarlarının yüzdesi için sayıları gösteren sütunlar içerir. Göstergedeki satırlar, azalan sırada, çekirdekler arası bağlam anahtarlarının sayısına göre sıralanır.

 Zaman çizelgesinde görüntülenen iş parçacıklarını filtrelemek için göstergedeki satırları seçebilirsiniz. Zaman çizelgesinde yalnızca seçili iş parçacıkları gösterilir. Satır seçili değilse, tüm satırlar zaman çizelgesinde gösterilir.

 Çapraz çekirdekli bağlam anahtarları, aynı mantıksal çekirdekte kalan anahtarlardan daha fazla ek yükü ve performansa mal olabilir. Bağlam anahtarları sırasında, işlemci kayıtları kaydedilir ve geri yüklenir, işletim sistemi çekirdeği kodu yürütülür, çeviri arabellek girişleri yeniden yüklenir ve işlemci ardışık düzeneği temizlenir. Önbellek verileri başka bir çekirdekteki bu iş parçacığı için geçerli olmadığından, çapraz çekirdekli bağlam anahtarları diğer bağlam anahtarlarından daha pahalı olabilir. Buna karşılık, bir iş parçacığı daha önce çalıştırdığı çekiüzerine bağlam açıksa, yararlı verilerin hala önbellekte olması olasıdır. İş parçacığı afiyetini ve performansı yönetme girişimleri yle çekirdekler arası bağlam anahtarları artırıldığında, bu sorunu giderip ele almamayı düşünün. İş parçacığı yakınlığını ortadan kaldırarak başlayın ve ardından ortaya çıkan çapraz çekirdek davranışını gözlemleyin.

 Aşağıdaki tabloda gösterge öğeleri açıklanmaktadır.

|Öğe|Tanım|
|-------------|----------------|
|İş Parçacığı Adı|Önceki çekirdek zaman çizelgesinde iş parçacığının rengini ve bu iş parçacığının adını gösterir.|
|Çapraz Çekirdek Liyak Anahtarları|Bir mantıksal çekirdekten diğerine de geçiş yapan bir iş parçacığı için bağlam anahtarları. Bir işlemciden diğerine geçen çapraz çekirdekli bağlam anahtarları ile aynı kalıpta kalanlar arasında ayrım yapmaz.|
|Toplam Bağlam Anahtarları|Örnekleme döneminde belirli bir iş parçacığı için toplam bağlam anahtarları. Bir iş parçacığı bağlamı her değiştirdiğinde (örneğin, yürütmeden eşitlemeye kadar) bir bağlam anahtarı sayılır.|
|Çekirdekleri ÇaprazLayan Bağlam Anahtarlarının Yüzdesi|Çekirdekler arası bağlam anahtarlarının sayısını toplam bağlam anahtarlarının sayısına bölerek yüzde olarak hesaplanır. Bu yüzde ne kadar yüksekse, çekirdekler arası bağlamın genel yükü bu özel iş parçacığının performansını değiştirir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çekirdekler Görünümü](../profiling/cores-view.md)