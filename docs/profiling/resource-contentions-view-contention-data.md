---
title: Kaynak çekişmeleri görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1607e594b6456d4da4396069d589160230b39680
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778342"
---
# <a name="resource-contentions-view---contention-data"></a>Kaynak Çakışmaları Görünümü - Çakışma Verileri
Kaynak Çekişmesi görünümü, çekişme olaylarının kaynağı olan kaynaklar için çekişme verilerini listeler. Başka bir iş parçacığında bir işlev kaynağa özel erişim elde ettiğinden, bir iş parçacığında bir işlev kaynağa erişim için beklemeye zorlandığında bir çekişme olayı oluşur. Her kaynak, çekişme olayları ile sonuçlanan işlev yürütme yollarını görüntüleyen bir çağrı ağacının kök düğümüdür.

## <a name="data-values"></a>Veri değerleri

### <a name="resource-values"></a>Kaynak değerleri
 Bir kaynak satırındaki veriler, profil oluşturma verilerinde kaynak erişimi engellenmiş toplam süreyi ve bu kaynağa erişim çakışması nedeniyle oluşan toplam çekişme olayı sayısını görüntüler. Bir kaynağın dahil ve dışlamalı değerleri her zaman aynıdır.

### <a name="function-values"></a>İşlev değerleri
 İşlev değerleri, çağrı ağacında temsil edilen yürütme yolunda oluşan işlevin örneklerine dayanır.

- Dışlamalı değerler, işlev gövdesinde deyimleri yürütürken oluşan olayları temel alır. İşlev tarafından çağrılan işlevlerde oluşan olaylar, Özel değerlere dahil edilmez.

- Kapsamlı değerler, işlev veya işlev tarafından çağrılan bir işlev çalıştırıldığında oluşan olayları temel alır.

### <a name="percentage-values"></a>Yüzde değerleri
 Yüzde değerleri, profil oluşturma verilerinde toplam süreyi veya çekişme olaylarını temel alır. Profil oluşturma çalıştırmasının raporuna veya görünümüne filtre uygulanmışsa, toplam değer olarak yalnızca filtrelenmiş verilerdeki engellenen süre ve çekişmeler kullanılır.

## <a name="navigating-the-resource-allocation-view"></a>Kaynak ayırma görünümünde gezinme

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Kaynak veya işlevin adı.|
|**Dışlamalı engellenme süresi**|-Bir kaynak için kaynağa erişen toplam süre engellenmiştir ve bir iş parçacığının beklenmesine neden oldu.<br />-Bir işlev için, işlevin işlev gövdesinde kod yürütürken, işlevin bu örneklerinin üst kaynağa erişmesi engellenmiş zaman. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.|
|**Dışlamalı engellenme süresi yüzdesi**|-Bir kaynak için, bu kaynağın engellenme süresi olan profil oluşturma verilerinde tüm engellenen sürenin yüzdesi<br />-Bir işlev için, bu işlev örneklerinin özel olarak engellenme süresi olan profil oluşturma verilerinde tüm engellenen sürenin yüzdesi.|
|**Dışlamalı çekişmeler**|-Bir kaynak için, kaynağa erişimin engellendiği ve bir iş parçacığının beklemesini neden olan toplam sayısı.<br />-Bir işlev için, işlevin işlev gövdesinde kod yürütürken, işlevin bu örneklerinin üst kaynağa erişmesi engellenecek olan sayı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil değildir.|
|**Dışlamalı çekişmeler yüzdesi**|-Bir kaynak için, bu kaynağa erişim için çekişme olayları olan profil oluşturma verilerinde bulunan tüm çekişme olaylarının yüzdesi.<br />-Bir işlev için, üst kaynak için bu işlev örneklerinin özel çekişme olayları olan profil oluşturma verilerinde bulunan tüm çekişme olaylarının yüzdesi.|
|**Kapsamlı engellenme süresi**|-Bir kaynak için kaynağa erişen toplam süre engellenmiştir ve bir iş parçacığının beklenmesine neden oldu.<br />-Bir işlev için, işlevin işlev gövdesinde kod yürütürken işlevin veya örneklerin tarafından çağrılan işlevlerin bu örneklerinin üst kaynağa erişmesi engellenir.|
|**Kapsamlı engellenme süresi%**|-Bir kaynak için, bu kaynağın engellenme süresi olan profil oluşturma verilerinde tüm engellenen sürenin yüzdesi<br />-Bir işlev için, bu işlev örneklerinin dahil olduğu, profil oluşturma çalıştırmasında engellenme süresi yüzdesi.|
|**Kapsamlı çekişmeler**|-Bir kaynak için, kaynağa erişimin engellendiği ve bir iş parçacığının beklemesini neden olan toplam sayısı.<br />-Bir işlev için, üst kaynak için bu işlev örneklerinin kapsamlı çekişme olayları olan profil oluşturma çalıştırmasında tüm çekişme olaylarının yüzdesi.|
|**Kapsamlı çekişmeler yüzdesi**|-Bir kaynak için, bu kaynağa erişim için çekişme olayları olan profil oluşturma çalıştırmasında tüm çekişme olaylarının yüzdesi.<br />-Bir işlev için, işlevin işlev gövdesinde kod yürütürken, işlevin bu örneklerinin üst kaynağa erişmesi engellenecek olan sayı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil değildir.|
|**Düzeyde**|Bu işlevin çağrı ağacındaki derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem KIMLIĞI**|İşlevin yürütüldüğü işlemin işlem KIMLIĞI (PID).|
|**İşlem adı**|İşlemin adı.|
|**Kaynak dosya**|Bu işlevin tanımını içeren kaynak dosya.|
