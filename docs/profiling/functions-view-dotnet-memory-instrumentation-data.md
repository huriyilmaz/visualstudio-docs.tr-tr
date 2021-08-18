---
title: İşlevler Görünümü - .NET Bellek Araçları Veri | Microsoft Docs
description: Ölçümleme yöntemi kullanılarak toplanan .NET bellek ayırma profili oluşturma verilerine ilişkin İşlevler görünümü hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ffac8904b22280e8dccc2e0aae96da780ff1b86e05b1b4ae10a9b504fe486cc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426969"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>İşlevler Görünümü - .NET bellek ölçüm verileri
Ölçümleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerine ilişkin İşlevler görünümü, profil oluşturma çalıştırması sırasında bellek ayrılan işlevleri listeler. İşlev satırı, ayırmaların boyutunu, sayısını ve işlevin zamanlama verilerini raporlar.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev Adı**|İşlevin adı.|
|**İşlev Adresi**|İşlevin adresi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan toplam çağrı sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Zaman Özel Yoklama Ek Yükü**|Ölçümleme nedeniyle bu işlevin zaman yükü. Yoklama ek yükü tüm dışlama zamanlarından çıkarıldı.|
|**Zaman Dahil Yoklama Ek Yükü**|Ölçümler nedeniyle bu işlev ve alt işlevleri için zaman yükü. Yoklama ek yükü tüm kapsayıcı zamanlardan çıkarıldı.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve onun alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmaları) ve boyutunu (bayt) belirtir.

 Özel bellek değerleri, alt işlevleri tarafından değil işlev tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Ayırmalar**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde oluşturulan nesnelerin toplam sayısı.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|İşlev, işlev gövdesinde kod yürütürken oluşturulan nesnelerin toplam sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve bu işlevin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde ayrılan bellek bayt sayısı.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı baytları olan tüm bellek baytlarının yüzdesi.|
|**Özel Bayt Sayısı**|Bu işlev tarafından ayrılan ancak bu işlev tarafından çağrılan işlevler tarafından olmayan bellek bayt sayısı.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin özel baytları olan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Saat %**|Bu işlevin geçen kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|Bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|Bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|Bu işleve yapılan bir çağrının geçen en düşük kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülmektedir zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda zaman içerir, ancak alt işlevlerde harcanan zamanı dahil değildir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|Bu işleve yapılan tüm çağrıların toplam özel süresi.|
|**Geçen Özel Saat %**|Bu işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|Bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**En Fazla Geçen Özel Süre**|Bu işleve yapılan bir çağrının geçen en uzun özel süresi.|
|**En Az Geçen Özel Süre**|Bu işleve yapılan bir çağrının geçen en düşük özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|Bu işleve yapılan tüm çağrıların toplam uygulama dahil süresi.|
|**Uygulama Dahil Saati %**|Bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının en uzun uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülebilir olduğu zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı veya alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|Bu işleve yapılan tüm çağrıların toplam uygulama özel süresi.|
|**Uygulamaya Özel Saat %**|Bu işlevin toplam uygulama özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu işleve yapılan bir çağrının ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu işleve yapılan bir çağrının en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu işleve yapılan bir çağrının uygulamaya özel en düşük süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
