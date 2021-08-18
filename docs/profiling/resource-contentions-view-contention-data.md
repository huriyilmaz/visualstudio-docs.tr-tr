---
title: Kaynak İçerikleri Görünümü - İçerik Verileri | Microsoft Docs
description: Kaynak İçeriği görünümünün, musiki olaylarının kaynağı olan kaynaklar için nasıl içerik verisi listele olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7848e4580bf7c5acdeca7edcebb20923d370af01dfd053e4b17234635fefa182
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442040"
---
# <a name="resource-contentions-view---contention-data"></a>Kaynak Çakışmaları Görünümü - Çakışma Verileri
Kaynak İhlali görünümü, musiki olaylarının kaynağı olan kaynaklar için içerikle ilgili verileri listeler. Başka bir iş parçacığında bir işlev kaynağa özel erişim elde etti olduğundan, bir iş parçacığında bir işlev kaynağa erişimi beklemek zorunda olduğunda bir sorun olayı oluşur. Her kaynak, bir çağrı ağacının, etkinlik olaylarının sonucunda ortaya çıkan işlev yürütme yollarını görüntüleyen kök düğümünü içerir.

## <a name="data-values"></a>Veri Değerleri

### <a name="resource-values"></a>Kaynak değerleri
 Kaynak satırdaki veriler, profil oluşturma verisinde kaynağa erişimin engellenmiş olduğu toplam zamanı ve bu kaynakla erişim çakışması nedeniyle meydana gelen çakışma olaylarının toplam sayısını görüntüler. Bir kaynak için kapsayıcı ve dış değerler her zaman aynıdır.

### <a name="function-values"></a>İşlev değerleri
 İşlev değerleri, çağrı ağacında temsil edilen yürütme yolunda meydana gelen işlev örneklerini temel almaktadır.

- Özel değerler, işlevin işlev gövdesinde deyimleri yürütürken meydana gelen olayları temel almaktadır. İşlev tarafından çağrılan işlevlerde meydana gelen olaylar özel değerlere dahil değildir.

- Kapsayıcı değerler, işlev veya işlev tarafından çağrılan bir işlev yürütücü olduğunda meydana gelen olaylara dayalıdır.

### <a name="percentage-values"></a>Yüzde değerleri
 Yüzde değerleri, profil oluşturma verisi içinde toplam zaman veya itiraz olaylarını temel alan değerlerdir. Profil oluşturma çalıştırması raporu veya görünümü filtrelenmişse, toplam değer olarak yalnızca filtrelenmiş verilerde engellenen süre ve içerikler kullanılır.

## <a name="navigating-the-resource-allocation-view"></a>Kaynak Ayırma Görünümü'nde Gezinme

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Kaynağın veya işlevin adı.|
|**Özel Engellenen Süre**|- Bir kaynak için kaynağa erişimin toplam süresi engellendi ve bir iş parçacığının beklemesi için neden oldu.<br />- bir işlev için işlev gövdesinde kod yürütürken işlevin bu örneklerinin üst kaynağa erişmesi engellenmiş olduğu zaman. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.|
|**Özel Engellenen Saat %**|- Bir kaynak için, profil oluşturma verisinde bu kaynağın süresi engellenen tüm zamanların yüzdesi<br />- Bir işlev için profil oluşturma verisinde bu işlev örneklerinin yalnızca engellenen süresi olan tüm engellenen sürelerin yüzdesi.|
|**Özel İçerikler**|- Bir kaynak için, kaynağa erişimin engellenmiş ve bir iş parçacığının beklemesi için neden olduğu toplam sayıdır.<br />- bir işlev için, işlev gövdesinde kod yürütürken işlevin bu örneklerinin üst kaynağa erişmesi engellenmiş sayısı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil değildir.|
|**Özel İçerik %**|- Bir kaynak için, profil oluşturma verisinde yer alan ve bu kaynağa erişim için olan tüm itiraz olaylarının yüzdesi.<br />- Bir işlev için, profil oluşturma verisinde yer alan ve üst kaynak için bu işlev örneklerinin özel olarak uzlastırma olayları olan tüm etkinlik olaylarının yüzdesi.|
|**Kapsayıcı Engellenen Süre**|- Bir kaynak için kaynağa erişimin toplam süresi engellendi ve bir iş parçacığının beklemesi için neden oldu.<br />- bir işlev için, işlev bu örneklerinin veya örnekler tarafından çağrılmış işlevlerin işlev gövdesinde kod yürütürken üst kaynağa erişmesi engellendi.|
|**Kapsayıcı Engellenen Saat %**|- Bir kaynak için, profil oluşturma verisinde bu kaynağın süresi engellenen tüm zamanların yüzdesi<br />- Bir işlev için profil oluşturma çalıştırması içinde engellenen tüm zamanların yüzdesi, bu işlev örneklerinin kapsayıcı engellenen süresidir.|
|**Kapsayıcı İçerikler**|- Bir kaynak için, kaynağa erişimin engellenmiş ve bir iş parçacığının beklemesi için neden olduğu toplam sayıdır.<br />- Bir işlev için, profil oluşturma çalışmalarında yer alan ve üst kaynak için bu işlev örneklerinin kapsayıcı muhtelemen olayları olan tüm etkinlik olaylarının yüzdesi.|
|**Kapsayıcı İçerik %**|- Bir kaynak için, profil oluşturma çalıştırması içinde yer alan ve bu kaynağa erişim için olan tüm itiraz olaylarının yüzdesi.<br />- bir işlev için, işlev gövdesinde kod yürütürken işlevin bu örneklerinin üst kaynağa erişmesi engellenmiş sayısı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil değildir.|
|**Düzey**|Bu işlevin çağrı ağacında derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|İşlevin yürütülmektedir işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
