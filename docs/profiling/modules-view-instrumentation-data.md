---
title: Modüller Görünümü - Ölçüm verisi | Microsoft Docs
description: Modüller görünümünün profil oluşturma verisinde yer alan modüllere göre gruplama yapan performans verilerini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9b2139b9483253507f926d9ac0ef37bba155f666
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107361"
---
# <a name="modules-view---instrumentation-data"></a>Modüller Görünümü - ölçüm verileri
Modüller görünümü, profil oluşturma verisinde yer alan modüllere göre gruplama yapan performans verilerini görüntüler. Modülün işlevleri modül düğümünün altında listelenir.

## <a name="general"></a>Genel
 Genel sütunlar, bir görünüm satırı içinde işlevini tanımladı.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin veya modülün adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve veya modüle yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Modülün veya işlevin yürütülmektedir işleminin adı.|
|**Zaman Özel Yoklama Ek Yükü**|Ölçümleme nedeniyle bu işlev veya modülün zaman yükü.|
|**Zaman Dahil Yoklama Ek Yükü**|Bu işlev veya modülün ve alt işlevlerinin zaman yükü, ölçümleme nedeniyle.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Bir işlev için işlevde harcanan süre. Bu, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Modül için, modülde en az bir işlevin çağrı yığınında olduğu süre.|
|**Geçen Kapsayıcı Saat %**|Bu modülün veya işlevin geçen toplam kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|- Bir işlev için bu işleve yapılan çağrının ortalama kapsayıcı süresi.<br />- Bir modül için modülde tüm işlevlere yapılan çağrıların ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|- Bir işlev için, bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en uzun geçen kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|- Bir işlev için bu modüle veya işleve yapılan çağrının en az geçen kapsayıcı süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülmektedir zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı dahil değildir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|- Bir işlev için modülde veya işlevde harcanan süre. Buna bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılar dahildir, ancak alt işlevlerde harcanan süre dışlar.<br />- Bir modül için, modülde işlevlerin geçen özel zamanlarının toplamı.|
|**Geçen Özel Saat %**|Bu modülün veya işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|- Bir işlev için bu işleve yapılan çağrının ortalama özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların ortalama özel süresi.|
|**En Fazla Geçen Özel Süre**|- Bir işlev için, bu işleve yapılan bir çağrının geçen en uzun özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en uzun geçen süresi.|
|**En Az Geçen Özel Süre**|- Bir işlev için, bu modüle veya işleve yapılan bir çağrının en az geçen özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en az geçen süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir. Ancak bu süre, alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|- bir işlev için, işleve yapılan çağrılarda harcanan süre. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları dışlar.<br />- Modül için, modülde en az bir işlevin çağrı yığınında olduğu süre. Bu, işletim sistemine yapılan çağrılarda harcanan zamanı dışlar.|
|**Uygulama Dahil Saati %**|Profil oluşturma çalıştırması için bu modülün veya işlevin uygulama dahil süresi içinde harcanan toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|- Bir işlev için bu işleve yapılan çağrının ortalama uygulama dahil süresi.<br />- Modül için, modülde işlevlere yapılan tüm çağrıların ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|- Bir işlev için, bu işleve yapılan bir çağrının en uzun uygulama dahil süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en uzun uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|- Bir işlev için bu modüle veya işleve yapılan çağrının en düşük uygulama dahil süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, modülde veya işlevde harcanan zamanı gösterir. Bu, alt işlevlerde harcanan zamanı dışlar ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|Bu modüle veya işleve yapılan tüm çağrıların toplam uygulama özel süresi.|
|**Uygulamaya Özel Saat %**|Bu modülün veya işlevin uygulama özel zamanlarında harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|-Bir işlev için, bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|-Bir işlev için, bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en fazla uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|-Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrılar için en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
- [Modüller görünümü-izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller görünümü-örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
