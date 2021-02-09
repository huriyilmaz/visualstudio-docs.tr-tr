---
title: Kaynak çakışması veri değerlerini anlama | Microsoft Docs
description: Bir uygulamadaki rekabet iş parçacıkları paylaşılan bir kaynağa erişim için beklemeye zorlandığında, kaynak çekişmenin profilini oluşturma hakkında ayrıntılı bilgiler toplar.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e050879fc9a1bd74f95ae5d24a92dc7a59a73c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886073"
---
# <a name="understand-resource-contention-data-values"></a>Kaynak çakışması veri değerlerini anlama

Kaynak Çekişmesi profili oluşturma, bir uygulamadaki rekabet iş parçacıklarının paylaşılan bir kaynağa erişim için beklemeye zorlanması durumunda ayrıntılı çağrı yığını bilgilerini toplar.

Kaynak çekişmeleri, modüller, işlevler, kaynak kodu satırları ve bekleme gerçekleştiği yönergelerin bir kaynağı beklerken harcanan toplam çekişme sayısını ve toplam süreyi görüntüler.

- Kapsamlı değerler, bir işlevi kaynak çekişmeleri ve işlevin bekleme toplam süresi tarafından beklemeye zorlayan toplam çekişmelerin sayısını görüntüler.  İşlev tarafından çağrılan alt işlevlerin neden olduğu çekişmeler, kapsamlı değerlere dahildir.

- Dışlamalı değerler yalnızca bir işlevin beklemesini ve işlevin gövdesinde kodun neden olduğunu zorlayan çekişmelerin sayısını görüntüler. Alt işlevlerin neden olduğu çekişmeler dahil değildir. İşlevin dışlamalı zamanı, yalnızca işlev gövdesinde deyimlerin neden olduğu bekleme sürelerini de içerir.

Kaynak çekişme raporu görünümleri Ayrıca zaman içinde bireysel çekişme olaylarını gösteren zaman çizelgesi grafiklerini içerir ve belirli bir olayı oluşturan çağrı yığınlarını gösterir. Daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [İş parçacığı Ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md)

- [Kaynak Ayrıntıları görünümü](../profiling/resource-details-view-contention-data.md)

Eşzamanlılık profili oluşturma işleminin ikinci modu hakkında daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md).
