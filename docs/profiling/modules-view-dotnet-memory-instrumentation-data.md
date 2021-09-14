---
title: Modüller Görünümü - .NET Bellek Araçları Veri | Microsoft Docs
description: Ölçüm yöntemi kullanılarak toplanan .NET bellek ayırma verileri modüller görünümünün bellek ve zamanlama verilerini modüle göre gruplamasını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4da8a05a9db7d10f149969ced9d1adcaf9a49c4e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626871"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modüller Görünümü - .NET bellek ölçüm verileri
Ölçüm yöntemi kullanılarak toplanan .NET bellek ayırma verileri Modüller görünümü, profil oluşturma çalıştırması içinde yürütülen modüller tarafından bellek ve zamanlama verilerini gruplar. Modülün işlevleri için profil oluşturma verileri modül düğümünün altında listelenir.

## <a name="general"></a>Genel

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
|**Zaman Dışlamalı Yoklama Ek Yükü**|Ölçümleme nedeniyle bu işlev veya modülün zaman yükü.|
|**Zaman Dahil Yoklama Ek Yükü**|Bu işlev veya modülün ve alt işlevlerinin zaman yükü, ölçümleme nedeniyle.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve onun alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmaları) ve boyutunu (bayt) belirtir.

 Özel bellek değerleri, alt işlevleri tarafından değil işlev tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir.

 Bir modülün kapsayıcı ve dış bellek değerleri, modülde yer alan işlevlerin kapsayıcı ve özel bellek değerlerinin toplamıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Ayırmalar**|- Bir işlev için, işlev tarafından oluşturulan nesnelerin toplam sayısı. Bu sayı, işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içerir.<br />- Bir modül için, bir profil oluşturma çalıştırması içinde modülden en az bir işlev yürütücü olduğunda ayrılan nesne sayısı. Bu sayı, modül işlevlerinden gelen çağrılar tarafından oluşturulan işlevlerde ayrılan nesneleri içerir.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün veya işlevin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|- Bir işlev için, işlev işlev gövdesinde kod yürütürken oluşturulan nesne sayısıdır (yani işlev çağrı yığınının en üstündeyken). Bu sayı, işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir modül için, modülde işlevlerin özel ayırmalarının toplamı.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün veya işlevin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Bayt Sayısı**|- Bir işlev için, işlev işlev gövdesinde kodu yürütürken ayrılan toplam bellek bayt sayısı (yani işlev çağrı yığınının en üstündeyken). Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />- Bir modül için, modülde işlevler tarafından ayrılan özel baytların toplamı.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün, işlevin, satırın veya yönergenin özel baytları olan tüm baytların yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|- Bir işlev için, işlev tarafından ayrılan bayt sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />- Bir modül için, modülden en az bir işlev yürüt edilirken ayrılan profil oluşturma çalıştırması içinde ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün veya işlevin kapsayıcı baytları olan tüm baytların yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- bir işlev için işlevde harcanan süre. Bu, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir modülde, modülde en az bir işlevin çağrı yığınında olduğu süre.|
|**Geçen Kapsayıcı Saat %**|Bu modül veya işlevin geçen toplam kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|- Bir işlev için bu işleve yapılan çağrının ortalama kapsayıcı süresi.<br />- Bir modül için modülde tüm işlevlere yapılan çağrıların ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|- Bir işlev için bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en uzun geçen kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Saat**|- Bir işlev için bu modüle veya işleve yapılan çağrının en az geçen kapsayıcı süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütül olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda zaman içerir, ancak alt işlevlerde harcanan zamanı dahil değildir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|- Bir işlev için modülde veya işlevde harcanan süre. Buna bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılar dahildir, ancak alt işlevlerde harcanan süre dışlar.<br />- Bir modül için, modülde işlevlerin geçen özel zamanlarının toplamı.|
|**Geçen Özel Saat %**|Bu modülün veya işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|- Bir işlev için bu işleve yapılan çağrının ortalama özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların ortalama özel süresi.|
|**En Fazla Geçen Özel Süre**|- Bir işlev için, bu işleve yapılan bir çağrının geçen en uzun özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en uzun geçen süresi.|
|**En Az Geçen Özel Süre**|- Bir işlev için, bu modüle veya işleve yapılan çağrının en az geçen özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en az geçen süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|- bir işlev için, işleve yapılan çağrılarda harcanan süre. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları dışlar.<br />- Bir modül için, işletim sistemine yapılan çağrılarda harcanan süre hariç olmak üzere modülde en az bir işlevin çağrı yığınında olduğu süre.|
|**Uygulama Dahil Saati %**|Profil oluşturma çalıştırması için bu modülün veya işlevin uygulama dahil süresi içinde harcanan toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|- Bir işlev için bu işleve yapılan çağrının ortalama uygulama dahil süresi.<br />- Modül için, modülde işlevlere yapılan tüm çağrıların ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|- Bir işlev için, bu işleve yapılan bir çağrının en uzun uygulama dahil süresi.<br />- Modül için, modülde işlevlere yapılan tüm çağrıların en uzun uygulama dahil süresi.|
|**En Az Uygulama Kapsayıcı Süresi**|- Bir işlev için bu modüle veya işleve yapılan çağrının en düşük uygulama dahil süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, alt işlevlerde harcanan süre hariç olmak üzere modülde veya işlevde harcanan zamanı gösterir. Belirtilen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|- Bir işlev için bu işleve yapılan çağrıların toplam uygulama özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların toplam uygulama özel süresi.|
|**Uygulamaya Özel Saat %**|Bu modülün veya işlevin uygulama özel zamanlarında harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|- Bir işlev için bu işleve yapılan çağrının ortalama uygulama özel süresi.<br />- Modül için, modülde işlevlere yapılan tüm çağrıların ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|- Bir işlev için, bu işleve yapılan bir çağrının en uzun uygulama özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların uygulama için en uzun süresi.|
|**En Az Uygulama Için Özel Süre**|- Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama özel süresi.<br />- Bir modül için, modülde işlevlere yapılan tüm çağrıların en düşük uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modüller Görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
