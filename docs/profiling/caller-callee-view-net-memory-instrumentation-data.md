---
title: Caller-Callee Görünümü - NET Bellek Araçları Veri | Microsoft Docs
description: Seçilen bir işlev ve bunun üst ve alt işlevleri için ayırma ve zamanlama verilerini gösteren .NET bellek profili oluşturma verileri için Arayan/Çağrılan görünümünü gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f3558ef81017fe382c5729003be8f1dd80978135
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136410"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Çağrılı görünümü - .NET bellek ölçüm verileri
Ölçümleme yöntemi kullanılarak toplanan .NET bellek profili oluşturma verisi Arayan/Çağrılı görünümü, seçili bir işlev için ayırma ve zamanlama verilerini ve seçili işlevin üst ve alt işlevlerini görüntüler. Çağıran/Çağrılı görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçilen işlevle ilgili bellek profili oluşturma bilgilerini gösterir. Değerler işleve yapılan tüm örnekli çağrıları içerir.

 **Geçerli işlevi çağıran** işlevler üst kılavuzda görüntülenir ve çağıranın (üst) işlevinden gelen çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından** çağrılan işlevler alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldıklarında seçili işlevin çağrılır (alt) işlevleri için bellek profili oluşturma verilerini gösterir.

 Bu satırı geçerli işlev yapmak için bir çağıranın veya çağrıyı yapan işlev satırına çift tıklayın.

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
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği.|
|**İşlem Adı**|İşleme atanan ad.|
|**Zaman Özel Yoklama Ek Yükü**|Ölçümleme nedeniyle bu işlevin zaman yükü. Yoklama ek yükü tüm dışlama zamanlarından çıkarıldı.|
|**Zaman Dahil Yoklama Ek Yükü**|Ölçümleme nedeniyle bu işlev ve alt işlevleri için zaman yükü. Yoklama ek yükü tüm kapsayıcı zamanlardan çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> **0** - geçerli işlev<br /><br /> **1** - geçerli işlevi çağıran bir işlev<br /><br /> **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök İşlev Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Ayırmalar**|- Geçerli işlev için, işlev işlev gövdesinde kod yürütürken oluşturulan nesne sayısı (yani işlev çağrı yığınının en üstündeyken). Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin özel ayırmalarının sayısı.<br />- Bir callee işlevi için, bu işlevin örnekleri tarafından oluşturulan ve geçerli işlev tarafından çağrılan nesne sayısı. Bu sayı, çağrılı işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve bu işlevin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsayıcı Ayırmalar**|- Geçerli işlev için, profil oluşturma çalıştırması içinde işlev tarafından ayrılan nesne sayısı. Sayı, işlev tarafından çağrılan çağrılım işlevlerinde oluşturulan nesneleri içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin kapsayıcı ayırmalarının sayısı.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Sayı, bu çağrı işlevinin çağıran işlevleri tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve bu işlevin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Bayt Sayısı**|- Geçerli işlev için, profil oluşturma çalıştırması içinde işlev tarafından ayrılan bellek bayt sayısı. Sayı, işlev tarafından çağrılan çağrılı işlevlerde ayrılan belleği içermez.<br />- Bir çağıranın işlevi için, bu çağıranın işlevi tarafından çağrılardan oluşturulan geçerli işlevin özel bayt sayısı.<br />- Bir çağrılı işlev için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, çağrıyıl işlevi tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin özel ayırmaları olan tüm bellek baytlarının yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|- Geçerli işlev için, profil oluşturma çalıştırması içinde işlev tarafından ayrılan bellekte bayt sayısı. Sayı, işlev tarafından çağrılan çağrılı işlevlerde ayrılan belleği içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin örneklerinin kapsayıcı bayt sayısı.<br />- Bir çağrılı işlev için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, bu çağrı işlevinin çağıran işlevleri tarafından ayrılan baytları içerir.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Geçerli işlev için işlevde harcanan süre. değeri, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen kapsayıcı süresi miktarı.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevde harcanan süre. değeri, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.|
|**Geçen Kapsayıcı Saat %**|Bu bağlamda bu işlevin geçen kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en az kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıların süresini içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|-Geçerli işlev için, işlevin gövdesinin yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan süreyi dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen dışlamalı süresinin miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, çağrılan işlevin alt işlevlerinde harcanan süreyi dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları içerir.|
|**Geçen dışlamalı süre yüzdesi**|Bu bağlamda bu işlevin toplam geçen dışlamalı süre içinde harcanan toplam çalışma zamanında geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|-Geçerli işlev için, işlevinde harcanan zaman ve alt işlevleri. Değer, işletim sistemine yapılan çağrılarında, bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan süreyi dışlar.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama kapsamlı süresi miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman ve geçerli işlevden çağrılar tarafından oluşturulan alt işlevleri. Değer, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez.|
|**Uygulama kapsamlı süresi%**|Bu bağlamda bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.|
|**En az uygulama kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulama dışlamalı değerleri, alt işlevlerde harcanan zamanı hariç olmak üzere işlevinde harcanan süreyi belirtir. Belirtilen zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi de dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|-Geçerli işlev için, işlevin gövdesinin yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dahil eder.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama dışlamalı zaman miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, çağrılan işlevin alt işlevlerinde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrı dahil eder.|
|**Uygulama dışlamalı süresi%**|Bu bağlamda bu işlevin toplam uygulama dışlamalı saatinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
