---
title: Caller-Callee görünümü-Izleme verileri | Microsoft Docs
description: Arayan/çağrılan görünümünün, Performans Gezgini arama ağacındaki izleme bilgilerini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de8e10c57bdf6278310467d3cf0505b9c8ce4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939495"
---
# <a name="callercallee-view---instrumentation-data"></a>Arayan/çağrılan görünümü-izleme verileri
Arayan/çağrılan görünümü seçili bir işlevle ilgili profil oluşturma bilgilerini ve çağrı ağacındaki üst ve alt işlevlerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlevle ilgili profil oluşturma bilgilerini gösterir. Değerler, işleve yapılan tüm çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve seçilen işlevin arayan (üst) işlevleriyle ilgili profil oluşturma bilgilerini gösterir. Değerler, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve seçilen işlevin aranan (alt) işlevlerinin örnekleri hakkındaki profil oluşturma bilgilerini gösterir. Değerler yalnızca, geçerli işlev tarafından çağrıldığında alt işlevde harcanan zamanı gösterir.

## <a name="general"></a>Genel
 Genel sütunlar, bir görünüm satırındaki işlevi belirler.

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
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev için, izleme nedeniyle oluşan zaman ek yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt işlevleri, izleme nedeniyle oluşur. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlev<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|-Geçerli işlev için, işlevde harcanan zaman. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen kapsamlı zaman miktarı.<br />-Aranan bir işlev için, bu işlevin geçerli işlevden çağrılar tarafından oluşturulan örneklerinde harcanan zaman. Değer, çağrılan ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıların alt işlevlerinde harcanan zamanı içerir.|
|**Geçen kapsamlı süre yüzdesi**|Bu bağlamda bu işlevin geçen iç zamanında harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen maksimum kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|-Geçerli işlev için, işlevin doğrudan yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen dışlamalı süresinin miktarı.<br />-Aranan bir işlev için, bu işlevin geçerli işlevden çağrılar tarafından oluşturulan örneklerinde harcanan zaman. Değer, çağrılan işlevin alt işlevlerinde harcanan süreyi dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları içerir.|
|**Geçen dışlamalı süre yüzdesi**|Bu bağlamda bu işlevin toplam geçen dışlamalı süre içinde harcanan toplam çalışma zamanında geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|-Geçerli işlev için, işlevinde harcanan zaman ve alt işlevleri. Değer, işletim sistemine yapılan çağrılarında, bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan süreyi dışlar.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama kapsamlı süresi miktarı.<br />-Aranan bir işlev için, bu işlevin geçerli işlevden çağrılar tarafından oluşturulan örneklerinde harcanan zaman. Değer, çağrılan işlevin alt işlevlerinde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez.|
|**Uygulama kapsamlı süresi%**|Bu bağlamda bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.|
|**En az uygulama kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulamanın dışlamalı değeri, işlevde harcanan süreyi belirtir. Bu, alt işlevlerde harcanan süreyi dışlar ve ayrıca, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|-Geçerli işlev için, işlevin doğrudan yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dahil eder.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama dışlamalı zaman miktarı.<br />-Aranan bir işlev için, bu işlevin geçerli işlevden çağrılar tarafından oluşturulan örneklerinde harcanan zaman. Değer, çağrılan işlevin alt işlevlerinde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrı dahil eder.|
|**Uygulama dışlamalı süresi%**|Bu bağlamda bu işlevin toplam uygulama dışlamalı saatinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Aranan görünümü-.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
