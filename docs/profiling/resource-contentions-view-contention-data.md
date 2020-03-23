---
title: Kaynak Çekişmeleri Görünümü - Çekişme Verileri | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778342"
---
# <a name="resource-contentions-view---contention-data"></a>Kaynak Çakışmaları Görünümü - Çakışma Verileri
Kaynak Çekişme görünümü, çekişme olaylarının kaynağı olan kaynaklar için çekişme verilerini listeler. Başka bir iş parçacığındaki bir işlev kaynağa özel erişim elde ettiğinden, iş parçacığındaki bir işlev kaynağa erişimi beklemek zorunda kaldığında bir çekişme olayı oluşur. Her kaynak, çekişme olaylarıyla sonuçlanan işlev yürütme yollarını görüntüleyen bir çağrı ağacının kök düğümüdür.

## <a name="data-values"></a>Veri Değerleri

### <a name="resource-values"></a>Kaynak değerleri
 Kaynak satırındaki veriler, profil oluşturma verilerinde kaynağa erişimin engellendiğinin toplam süresini ve bu kaynağa erişim çakışması nedeniyle oluşan toplam çekişme olayı sayısını görüntüler. Bir kaynak için kapsayıcı ve özel değerler her zaman aynıdır.

### <a name="function-values"></a>İşlev değerleri
 İşlev değerleri, çağrı ağacında temsil edilen yürütme yolunda gerçekleşen işlev örneklerini temel alın.

- Özel değerler, işlev işlev gövdesinde deyimleri yürütürken meydana gelen olaylara dayanır. İşlev tarafından çağrılan işlevlerde oluşan olaylar özel değerlere dahil edilmez.

- Kapsayıcı değerler, işlev veya işlev tarafından çağrılan bir işlev yürütüldüğünde meydana gelen olaylara dayanır.

### <a name="percentage-values"></a>Yüzde değerleri
 Yüzde değerleri, profil oluşturma verilerindeki toplam zaman veya çekişme olaylarını temel alar. Profil oluşturma çalışmasının raporu veya görünümü filtrelenirse, toplam değer olarak yalnızca engellenen süre ve filtreuygulanmış verilerdeki çekişmeler kullanılır.

## <a name="navigating-the-resource-allocation-view"></a>Kaynak Ayırma Görünümünde Gezinme

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Kaynak veya işlevin adı.|
|**Özel Engellenen Süre**|- Bir kaynak için, kaynağa erişimin engellediği toplam süre ve iş parçacığının beklemesine neden oldu.<br />- Bir işlev için, işlevin işlev gövdesinde kod yürütüldüğünde bu örneklerin ana kaynağa erişilmesi engellenir. İşlev tarafından çağrılan işlevlerde engellenen süre dahil edilmez.|
|**Özel Engellenen Süre %**|- Bir kaynak için, bu kaynağın engellenen zaman profil oluşturma verilerinde tüm engellenen zaman yüzdesi<br />- Bir işlev için, bu işlev örneklerinin münhasır engellenen zamanı olan profil oluşturma verilerindeki tüm engellenen zamanın yüzdesi.|
|**Özel Çekişmeler**|- Bir kaynak için, kaynağa erişimin toplam sayısı engellendi ve iş parçacığının beklemesine neden oldu.<br />- Bir işlev için, işlev işlevi işlevi gövdesinde kod yürütüldüğünde, işlevin bu örneklerinin ana kaynağa erişmesinin engellenme sayısı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil edilmez.|
|**Özel Çekişmeler %**|- Bir kaynak için, bu kaynağa erişim için çekişme olayları olan profil oluşturma verilerindeki tüm çekişme olaylarının yüzdesi.<br />- Bir işlev için, üst kaynak için bu işlev örneklerinin özel çekişme olayları olan profil oluşturma verilerindeki tüm çekişme olaylarının yüzdesi.|
|**Kapsayıcı Engellenen Süre**|- Bir kaynak için, kaynağa erişimin engellediği toplam süre ve iş parçacığının beklemesine neden oldu.<br />- Bir işlev için, işlevin bu örneklerinin veya örnekler tarafından çağrılan işlevlerin işlev gövdesinde kod yürütüldüğünde ana kaynağa erişilmesiengellenmiş olan süre.|
|**Kapsayıcı Engellenen Süre %**|- Bir kaynak için, bu kaynağın engellenen zaman profil oluşturma verilerinde tüm engellenen zaman yüzdesi<br />- Bir işlev için, bu işlev örneklerinin kapsayıcı engellenmiş zamanı olan profil oluşturma çalışmasındaki tüm engellenen zamanın yüzdesi.|
|**Kapsayıcı Çekişmeler**|- Bir kaynak için, kaynağa erişimin toplam sayısı engellendi ve iş parçacığının beklemesine neden oldu.<br />- Bir işlev için, profil oluşturma çalışmasındaki tüm çekişme olaylarının yüzdesi, üst kaynak için bu işlev örneklerinin kapsayıcı çekişme olaylarıdır.|
|**Kapsayıcı Çekişmeler %**|- Bir kaynak için, profil oluşturma çalışmasındaki tüm çekişme olaylarının yüzdesi, bu kaynağa erişim için çekişme olaylarıdır.<br />- Bir işlev için, işlev işlevi işlevi gövdesinde kod yürütüldüğünde, işlevin bu örneklerinin ana kaynağa erişmesinin engellenme sayısı. İşlev tarafından çağrılan işlevlerde engelleme olayları dahil edilmez.|
|**Düzey**|Arama ağacındaki bu işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|İşlevin yürütüldettiği işlemin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
