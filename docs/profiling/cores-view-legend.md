---
title: Çekirdekler Görünümü Gösterge | Microsoft Docs
description: Tablosal bağlam anahtarı verileri ve iş parçacığı seçimi sağlayan Çekirdek görünümü göstergesini öğrenin. Bağlam anahtarları ve performans hakkında da bilgi edinmek.
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
ms.openlocfilehash: 2b02000164ddea2d10cbe33a5f95f158f617ea383815a8691bd215b6a0424663
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333476"
---
# <a name="cores-view-legend"></a>Çekirdekler Görünümü gösterge
Çekirdekler Görünümü gösterge, her iş parçacığını renge ve ada göre tanımlar. Çekirdekler arası bağlam anahtarları, toplam bağlam anahtarları ve çekirdekler arasında bağlam anahtarlarının yüzdesini içeren sütunlar içerir. Göstergede satırlar, azalan düzende çekirdekler arası bağlam anahtarları sayısına göre sıralanmış.

 Zaman çizelgesinde görüntülenen iş parçacıklarını filtrelemek için göstergede satırlar seçin. Zaman çizelgesinde yalnızca seçilen iş parçacıkları gösterilir. Satır seçilmezse, zaman çizelgesinde tüm satırlar gösterilir.

 Çekirdekler arası bağlam anahtarları, aynı mantıksal çekirdekte kalan anahtarlardan daha fazla ek yük ve performans maliyetine sahiptir. Bağlam anahtarları sırasında işlemci kayıtları kaydedilir ve geri yüklenir, işletim sistemi çekirdek kodu yürütülür, çeviri tarafı arabellek girişleri yeniden yüklenir ve işlemci işlem hattı boşaltıldı. Önbellek verileri başka bir çekirdekte bu iş parçacığı için geçerli olduğundan, çekirdekler arası bağlam anahtarları diğer bağlam anahtarlardan daha pahalı olabilir. Buna karşılık, bir iş parçacığı daha önce üzerinde üzerinde çalışma yaptığı çekirdek üzerinde bağlamla değiştirildi ise, yararlı veriler hala önbellektedir. İş parçacığı benzitesini yönetme girişimleriyle çekirdekler arası bağlam anahtarları artırıldı ve performans düşük olduğunda, bu sorunu ele alıp ele alamayabilirsiniz. başlangıç olarak iş parçacığı benzeşmsini ortadan kaldırın ve sonra sonuçta elde edilen çekirdekler arası davranışı gözlemler.

 Aşağıdaki tabloda açıklama öğeleri açık almaktadır.

|Öğe|Tanım|
|-------------|----------------|
|İş Parçacığı Adı|Önceki çekirdek zaman çizelgesinde iş parçacığının rengini ve bu iş parçacığının adını gösterir.|
|Çekirdekler Arası Bağlam Anahtarları|Bir mantıksal çekirdekten diğerine geçiş yapılan bir iş parçacığı için bağlam anahtarlarının sayısı. Çekirdekler arası bağlam anahtarları ile bir işlemciden diğerine çapraz geçiş yapanlar ile aynı kalıpta kalmayanlar arasında ayrım yapmak zorunda değildir.|
|Toplam Bağlam Anahtarları|Örnekleme dönemi boyunca verilen bir iş parçacığı için bağlam anahtarlarının toplam sayısı. Bir iş parçacığı bağlamı her değiştirse (örneğin, yürütmeden eşitlemeye) bir bağlam anahtarı sayılır.|
|Çekirdekler Arasında Bağlam Anahtarlarının Yüzdesi|Çekirdekler arası bağlam anahtarları sayısının toplam bağlam anahtarı sayısına bölünmesi ile yüzde olarak hesaplanır. Bu yüzde ne kadar yüksekse, çekirdekler arası bağlam ek yükünün genel etkisi bu iş parçacığının performansına ne kadar büyük bir etki gösterir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çekirdekler Görünümü](../profiling/cores-view.md)