---
title: Özet görünümü-kaynak çakışması görünümü | Microsoft Docs
description: Özet görünümü, uygulamanızda bir iş parçacığı veya işlemin askıya alındığı, bir kaynağa erişmeyi beklerken, uygulamanızdaki olaylar hakkındaki bilgileri görüntüler.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3e6f0b629aa14cf465dcaa8abec48e3eea110c4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960006"
---
# <a name="summary-view---resource-contention-view"></a>Özet Görünümü - Kaynak Çakışması Görünümü
Özet görünümü, uygulamanızda bir iş parçacığı veya işlemin askıya alındığı, bir kaynağa erişmeyi beklerken, uygulamanızdaki olaylar hakkındaki bilgileri görüntüler.

 Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Zaman çizelgesi grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturma işleminin gerçekleştiği zaman içindeki profili oluşturulan uygulamanın çekişme olaylarının sayısını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>En fazla Contenbitmiş kaynaklar
 **En fazla çekişme kaynağı** , uygulamadaki en fazla çekişme olayına neden olan kaynakları listeler. Çekişmeler görünümünü görüntülemek için bir kaynak adına tıklayabilirsiniz. Çekişmeler görünümü iş parçacığına göre kaynak çekişmelerinin ayrıntılı bir zaman çizelgesini sağlar.

 **En çok kullanılan kaynaklar** , her kaynak için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Kaynağın adı.|
|**Çekişme**|Bu kaynak üzerinde çekişmeler olan profil oluşturma verilerinde bulunan tüm çekişme olaylarının yüzdesi.|

## <a name="most-contended-thread"></a>En fazla Contensonlandırılan Iş parçacığı
 **En fazla Contensonlanma Iş parçacıkları** uygulamadaki en fazla çekişme olay sayısına sahip iş parçacıklarını listeler. İş parçacığının kaynak çekişmelerinin ayrıntılı bir zaman çizelgesini sağlayan çekişmeler görünümünü görüntülemek için bir iş parçacığı adına tıklayabilirsiniz.

 **En çok Iş parçacığı sayısı** , her iş parçacığı için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**ID**|İş parçacığı tanımlayıcısı.|
|**Ad**|İş parçacığına sahip olan işlemin adı.|
|**Çekişme**|Bu kaynak üzerinde çekişmeler olan profil oluşturma verilerinde bulunan tüm çekişme olaylarının yüzdesi.|
