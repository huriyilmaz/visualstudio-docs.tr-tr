---
title: Kaynak Çekişmesi Veri Değerlerini Anlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f522d1854cae86d9dc6e757ef0c9a62f4511800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779993"
---
# <a name="understand-resource-contention-data-values"></a>Kaynak çekişme veri değerlerini anlama

Kaynak çekişmesi profil oluşturma, bir uygulamada rakip iş parçacıkları paylaşılan bir kaynağa erişim beklemek zorunda her zaman ayrıntılı arama yığını bilgileri toplar.

Kaynak çekişme raporları, toplam çekişme sayısını ve beklemenin gerçekleştiği modüller, işlevler, kaynak kodu satırları ve yönergeleri için kaynak beklerken harcanan toplam zamanı görüntüler.

- Kapsayıcı değerler, bir işlevi kaynak çekişmelerine göre beklemeye zorlayan toplam çekişme sayısını ve işlevin beklediği toplam süreyi görüntüler.  İşlev tarafından çağrılan alt işlevler tarafından neden olduğu çekişmeler kapsayıcı değerlere dahil edilir.

- Özel değerler yalnızca bir işlevi beklemeye zorlayan ve işlevin gövdesindeki koddan kaynaklanan çekişme sayısını görüntüler. Alt işlevlerden kaynaklanan çekişmeler dahil edilmez. İşlev için özel süre, yalnızca işlev gövdesindeki ifadelerden kaynaklanan bekleme sürelerini de içerir.

Kaynak çekişme raporu görünümleri, zaman içinde tek tek çekişme olaylarını gösteren ve belirli bir olayı oluşturan çağrı yığınlarını gösteren zaman çizelgesi grafiklerini de içerir. Daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [İş parçacığı ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md)

- [Kaynak ayrıntıları görünümü](../profiling/resource-details-view-contention-data.md)

Eşzamanlılık profillemenin ikinci modu hakkında daha fazla bilgi için [Concurrency Visualizer](../profiling/concurrency-visualizer.md)bölümüne bakın.
