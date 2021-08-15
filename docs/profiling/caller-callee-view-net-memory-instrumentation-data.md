---
title: Caller-Callee görünümü-NET bellek Izleme verileri | Microsoft Docs
description: Seçilen bir işlev için ayırma ve zamanlama verilerini ve bunun üst ve alt işlevlerini gösteren .NET bellek profili oluşturma verilerinin arayan/çağrılan görünümünü gözden geçirin.
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
ms.openlocfilehash: 3615ce4ae26c7fdd3d4473f9abf3076df0ee830bde1e8449278c901245dbdc5f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257348"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Aranan görünümü-.NET bellek izleme verileri
İzleme yöntemi kullanılarak toplanan .NET bellek profili oluşturma verilerinin arayan/çağrılan görünümü seçili bir işlev için ayırma ve zamanlama verilerini ve seçilen işlevin üst ve alt işlevlerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlevle ilgili bellek profili oluşturma bilgilerini gösterir. Değerler, işleve tüm örneklenmiş çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve çağıran (üst) işlevden çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine yönelik bellek profili oluşturma verilerini gösterir.

 Bu satırı geçerli işlev haline getirmek için bir arayan veya çağrılan işlev satırına çift tıklayın.

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
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI.|
|**İşlem adı**|İşleme atanan ad.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlevin izleme nedeniyle zaman yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt öğesi izleme nedeniyle alt işlevleri. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlev<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı ayırmalar**|-Geçerli işlev için, işlev gövdesinde kod yürütürken oluşturulan nesne sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Numara, bu işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin özel ayırmaların sayısı.<br />-Bir çağrılan işlev için, bu işlevin geçerli işlev tarafından çağrılan örnekleri tarafından oluşturulan nesne sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Dışlamalı ayırmalar%**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Kapsamlı ayırmalar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan nesne sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin dahil olduğu ayırmaların sayısı.<br />-Bir çağrılan işlev için, geçerli işlevden çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, bu çağrılan işlev tarafından çağrılan işlevlerin yaptığı ayırmaları içerir.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı baytlar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde ayrılan belleği içermez.<br />-Çağıran işlevi için, bu çağıran işlev tarafından yapılan çağrılardan oluşturulan geçerli işlevin özel bayt sayısı.<br />-Bir çağrılan işlev için, bu işlevin, geçerli işlevden çağrılar tarafından oluşturulan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Kapsamlı baytlar**|-Geçerli işlev için, bellekteki, profil oluşturma çalıştırmasında ayrılan bayt sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde ayrılan belleği içerir.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin örneklerinin dahil edilen bayt sayısı.<br />-Bir çağrılan işlev için, bu işlevin, geçerli işlevden çağrılar tarafından oluşturulan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, bu çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içerir.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|-Geçerli işlev için, işlevde harcanan zaman. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen kapsamlı zaman miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen kapsamlı süre yüzdesi**|Bu bağlamda bu işlevin geçen iç zamanında harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen maksimum kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülmektedir zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda zaman içerir, ancak alt işlevlerde harcanan zamanı dahil değildir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|- Geçerli işlev için, işlevin gövdesinin yürütülmesinde harcanan süre. değeri, alt işlevlerde harcanan zamanı hariç tutsa da bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen özel süresi miktarı.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevde harcanan süre. değeri, çağrılan işlevinin alt işlevlerinde harcanan zamanı dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen Özel Saat %**|Bu bağlamda bu işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının ortalama özel süresi.|
|**En Fazla Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun özel süresi.|
|**En Az Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en düşük özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|- Geçerli işlev için, işlevde ve onun alt işlevlerinde harcanan süre. değeri, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dışlar.<br />- Çağıran işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin uygulama dahil süresi.<br />- Bir çağrılı işlev için, bu işlevde harcanan süre ve geçerli işlevden yapılan çağrılar tarafından oluşturulan alt işlevleri. değeri, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir.|
|**Uygulama Dahil Saati %**|Bu bağlamda bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, alt işlevlerde harcanan süre hariç olmak üzere işlevde harcanan zamanı gösterir. Belirtilen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|- Geçerli işlev için, işlevin gövdesinin yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin uygulamanın özel süresi.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevde harcanan süre. Değer, çağrıyı çağıran işlevinin alt işlevlerine harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.|
|**Uygulamaya Özel Saat %**|Bu bağlamda, bu işlevin toplam uygulama özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl ekleyebilirsiniz: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Çağrılı görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Çağrılı görünümü - ölçüm verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Arayan/Çağrılı görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
