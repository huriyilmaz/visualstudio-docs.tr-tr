---
title: Modüller görünümü-.NET bellek Izleme verileri | Microsoft Docs
description: İzleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin modüller görünümünün, bellek ve zamanlama verilerini modüle göre gruplayarak bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: e6a0a42fdc83891b96bb3fe036ebf7515e3d6a42
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723315"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modüller görünümü-.NET bellek izleme verileri
İzleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin Modüller görünümü, profil oluşturma çalıştırmasında yürütülen modüller tarafından bellek ve zamanlama verilerini gruplandırır. Modülün işlevleri için profil oluşturma verileri modül düğümünün altında listelenmiştir.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin veya modülün adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Çağrı Sayısı**|Bu işlev veya modüle yapılan toplam çağrı sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Modülün veya işlevin yürütüldüğü işlemin adı.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev veya modül için izleme nedeniyle zaman yükü.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev veya modülle ilgili zaman yükü ve izleme nedeniyle alt işlevleri.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsamlı .NET bellek değerleri, işlev ve alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmaları) ve boyutunu (bayt) gösterir.

 Dışlamalı bellek değerleri, işlev tarafından oluşturulan ve alt işlevlerine göre değil, nesne sayısını ve boyutunu belirtir.

 Modülün dahil ve dışlamalı bellek değerleri, modüldeki işlevlerin dahil ve dışlamalı bellek değerlerinin toplamıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsamlı ayırmalar**|-Bir işlev için, işlev tarafından oluşturulan toplam nesne sayısı. Bu sayı, işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü zaman ayrılan bir profil oluşturma çalıştırmasında nesne sayısı. Bu sayı, modül işlevlerinden çağrılar tarafından oluşturulan işlevlerde ayrılan nesneleri içerir.|
|**Kapsamlı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan, modülün veya işlevin kapsamlı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|-Bir işlev için, işlev gövdesinde kod yürütürken oluşturulan nesne sayısı (işlev, çağrı yığınının en üstünde olduğunda). Bu sayı, işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Bir modül için, modüldeki işlevlerin dışlamalı ayırmaların toplamı.|
|**Dışlamalı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan ve modülün veya işlevin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Dışlamalı baytlar**|-Bir işlev için, işlev gövdesinde kod yürütürken ayrılan belleğin toplam bayt sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />-Bir modül için, modüldeki işlevlerle ayrılan özel baytlar toplamı.|
|**Dışlamalı bayt yüzdesi**|Profil oluşturma çalıştırmasında ayrılan ve modülün, işlevin, çizginin veya yönergenin özel baytları olan tüm baytların yüzdesi.|
|**Kapsamlı baytlar**|-Bir işlev için, işlev tarafından ayrılan bayt sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü zaman ayrılan bir profil oluşturma çalıştırmasında ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.|
|**Dahil edilen baytlar%**|Profil oluşturma çalıştırmasında ayrılan ve modülün veya işlevin kapsamlı baytları olan tüm baytların yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|-Bir işlev için, işlevde harcanan zaman. Bu, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir modül için, modüldeki en az bir işlevin çağrı yığınında olduğu zaman dilimi.|
|**Geçen kapsamlı süre yüzdesi**|Bu modülün veya işlevin toplam geçen kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen ortalama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen ortalama kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen en uzun kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen maksimum kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|-Bir işlev için, bu modül veya işlev çağrısının geçen en düşük kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen minimum kapsamlı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıların süresini içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|-Bir işlev için, modülde veya işlevinde harcanan zaman. Bu, işletim sistemine çağrı içerir (bağlam anahtarları ve giriş/çıkış işlemleri gibi), ancak alt işlevlerde harcanan süreyi dışlar.<br />-Bir modül için, modüldeki işlevlerin geçen dışlamalı saatlerin toplamı.|
|**Geçen dışlamalı süre yüzdesi**|Bu modülün veya işlevin toplam geçen dışlamalı süre içinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|-Bir işlev için, bu işleve yapılan çağrının ortalama hariç geçen süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama hariç geçen süresi.|
|**Geçen maksimum dışlamalı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrılar için geçen maksimum dışlamalı süre.|
|**Geçen en düşük dışlamalı süre**|-Bir işlev için, bu modül veya işlev çağrısının en az bir özel süresi geçti.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en düşük özel süresi geçti.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|-Bir işlev için, işlev çağrılarında harcanan zaman. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dışlar.<br />-Bir modül için, modüldeki en az bir işlevin çağrı yığınında olması, işletim sistemine yapılan çağrılarda harcanan zaman hariç olmak üzere zaman dilimi.|
|**Uygulama kapsamlı süresi%**|Bu modülün veya işlevin uygulama kapsamlı sırasında harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|-Bir işlev için, bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|-Bir işlev için, bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en fazla uygulama kapsamlı süresi.|
|**En az uygulama kapsamlı süre**|-Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulama dışlamalı değeri, alt işlevlerde harcanan zaman hariç olmak üzere, modülde veya işlevde harcanan süreyi belirtir. Belirtilen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|-Bir işlev için, bu işleve yapılan çağrıların Toplam uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların Toplam uygulama dışlamalı süresi.|
|**Uygulama dışlamalı süresi%**|Bu modülün veya işlevin uygulama dışlamalı sırasında harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|-Bir işlev için, bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|-Bir işlev için, bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en fazla uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|-Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrılar için en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modüller görünümü-örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
