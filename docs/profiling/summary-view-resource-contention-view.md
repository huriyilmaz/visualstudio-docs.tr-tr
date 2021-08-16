---
title: Özet Görünümü - Kaynak İçeriği Görünümü | Microsoft Docs
description: Özet görünümü, uygulamanıza bir iş parçacığının veya sürecin bir kaynağa erişim için beklerken askıya alınarak askıya alınmış olaylarla ilgili bilgileri görüntüler.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ad4fe35610aa7204d21d70a2454a3a6a5a52e3391a16f6f8cfd4fc0fe516ce97
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410235"
---
# <a name="summary-view---resource-contention-view"></a>Özet Görünümü - Kaynak Çakışması Görünümü
Özet görünümü, uygulamanıza bir iş parçacığının veya sürecin bir kaynağa erişim için beklerken askıya alınarak askıya alınmış olaylarla ilgili bilgileri görüntüler.

 Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için bkz. [Özet Görünümü.](../profiling/summary-view.md)

## <a name="timeline-graph"></a>Zaman çizelgesi Graph
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın meydana geldiği zaman içinde profili yapılan uygulamanın olaylarının sayısını gösterir. Zaman çizelgesi grafiğini kullanarak görünümü seçilen bir zaman aralığına göre filtre görebilirsiniz. Daha fazla bilgi için, [bkz. How to: Filter Report Views from the Summary Timeline](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>En Çok Mücadele Edilen Kaynaklar
 **En Çok Yarışan** Kaynaklar, uygulama içinde en fazla soruna neden olan kaynakları listeler. Bir kaynak adına tıklar ve İçerikler görünümünü görüntüebilirsiniz. İçerikler görünümü, iş parçacığına göre kaynak içeriklerinin ayrıntılı bir zaman çizelgesini sağlar.

 **En Çok Kullanılan Kaynaklar** her kaynak için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Kaynağın adı.|
|**İçerik %**|Profil oluşturma verisi içinde yer alan ve bu kaynak üzerinde yapılan tüm itiraz olaylarının yüzdesi.|

## <a name="most-contended-thread"></a>En Çok Mücadele Edilen İş Parçacığı
 **En Çok Yarışan** İş Parçacıkları, uygulama içinde en fazla sayıdaki musiki olaylarına sahip olan iş parçacıklarını listeler. İş parçacığına göre kaynak içeriklerinin ayrıntılı zaman çizelgesini sağlayan İçerikler görünümünü görüntülemek için bir iş parçacığı adına tıkabilirsiniz.

 **En Çok Yarışan İş** Parçacıkları, her iş parçacığı için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**ID**|İş parçacığı tanımlayıcısı.|
|**Ad**|İş parçacığına sahip olan sürecin adı.|
|**İçerik %**|Profil oluşturma verisi içinde yer alan ve bu kaynak üzerinde yapılan tüm itiraz olaylarının yüzdesi.|
