---
title: Kaynak İçeriği Veri Değerlerini Anlama | Microsoft Docs
description: Kaynak rekabeti profili oluşturmanın, bir uygulamada iş parçacıklarının paylaşılan bir kaynağa erişmeyi beklemek zorunda olduğu zaman nasıl ayrıntılı bilgi toplayanı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b397a3171cc03822271224679e2792da6d5e3f5a821f58cb5ec19707288bc202
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230956"
---
# <a name="understand-resource-contention-data-values"></a>Kaynakla ilgili veri değerlerini anlama

Kaynak rekabeti profili oluşturma, bir uygulama içinde rakip iş parçacıkları paylaşılan bir kaynağa erişimi beklemek zorunda kalan her sefer ayrıntılı çağrı yığını bilgilerini toplar.

Kaynak İhlal raporları modüller, işlevler, kaynak kod satırları ve beklemenin meydana geldiği yönergeler için kaynağı beklerken harcanan toplam süre ve toplam irdelez sayısını görüntüler.

- Kapsayıcı değerler, bir işlevi kaynak karşıtlıkları tarafından beklemeye zorlanan toplam içerik sayısını ve işlevin beklediği toplam zamanı görüntüler.  İşlev tarafından çağrılan alt işlevlerden kaynaklanan içerikler kapsayıcı değerlere dahil edilir.

- Özel değerler yalnızca bir işlevi beklemeye zorlanan ve işlevin gövdesinde yer alan koddan kaynaklanan içerik sayısını görüntüler. Alt işlevlerin neden olduğu içerikler dahil değildir. İşlev için özel zaman yalnızca işlev gövdesinde deyimlerin neden olduğu bekleme sürelerini de içerir.

Kaynak tartışma raporu görünümleri ayrıca zaman içinde tek tek tartışma olaylarını ve belirli bir olayı oluşturan çağrı yığınlarını göstermek için zaman çizelgesi grafikleri içerir. Daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [İş parçacığı ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md)

- [Kaynak ayrıntıları görünümü](../profiling/resource-details-view-contention-data.md)

İkinci eşzamanlılık profili oluşturma modu hakkında daha fazla bilgi için [bkz. Eşzamanlılık Görselleştiricisi.](../profiling/concurrency-visualizer.md)
