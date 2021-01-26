---
title: İşlevler görünümü-.NET bellek Izleme verileri | Microsoft Docs
description: İzleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Işlevler görünümü hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 5a245ebffc0aa0efaec8df1ec0c5b93b2d99228d
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801532"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>İşlevler görünümü-.NET bellek izleme verileri
İzleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Işlevleri, profil oluşturma çalışması sırasında belleği ayrılan işlevleri listeler. İşlev satırı, ayırma boyutunu ve sayısını ve işlevin zamanlama verilerini raporlar.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev adı**|İşlevin adı.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlevin izleme nedeniyle zaman yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt öğesi izleme nedeniyle alt işlevleri. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsamlı .NET bellek değerleri, işlev ve alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmaları) ve boyutunu (bayt) gösterir.

 Dışlamalı bellek değerleri, işlev tarafından oluşturulan ve alt işlevlerine göre değil, nesne sayısını ve boyutunu belirtir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsamlı ayırmalar**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde oluşturulan toplam nesne sayısı.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|İşlev gövdesinde kod yürütürken oluşturulan toplam nesne sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.|
|**Dışlamalı ayırmalar%**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Kapsamlı baytlar**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde ayrılan bellek bayt sayısı.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Dışlamalı baytlar**|Bu işlev tarafından ayrılan ancak bu işlev tarafından çağrılan işlevlere göre olmayan belleğin bayt sayısı.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|Bu işleve yapılan çağrıların toplam geçen kapsamlı süresi.|
|**Geçen kapsamlı süre yüzdesi**|Bu işlevin geçen kapsamlı sürede harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu işleve yapılan çağrının geçen en uzun kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıların süresini içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|Bu işleve yapılan tüm çağrıların geçen toplam dışlamalı süresi.|
|**Geçen dışlamalı süre yüzdesi**|Bu işlevin geçen toplam kullanım süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu işlev çağrısının geçen maksimum dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|Bu işleve yapılan tüm çağrıların Toplam uygulama kapsamlı süresi.|
|**Uygulama kapsamlı süresi%**|Bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu işleve yapılan çağrının uygulama kapsamlı en fazla süresi.|
|**En az uygulama kapsamlı süre**|Bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulamanın dışlamalı değeri, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez ve alt işlevlerde harcanan zamanı dahil etmez.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|Bu işleve yapılan tüm çağrıların Toplam uygulama dışlamalı süresi.|
|**Uygulama dışlamalı süresi%**|Bu işlevin toplam uygulama dışlamalı saatinde harcanan profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü-Örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
