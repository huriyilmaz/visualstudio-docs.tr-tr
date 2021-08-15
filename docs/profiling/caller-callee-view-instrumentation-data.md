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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9abef15506a3d44dad2ff44b4ac6f425dc02f6fd35c2babe4b27ff964b783733
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427190"
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
|**Ortalama uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, işlevde harcanan zamanı gösterir. Bu, alt işlevlerde harcanan zamanı dışlar ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|- Geçerli işlev için, işlevin doğrudan yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin uygulamanın özel süresi.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örneklerde harcanan süre. Değer, çağrıyı çağıran işlevinin alt işlevlerine harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.|
|**Uygulamaya Özel Saat %**|Bu bağlamda, bu işlevin toplam uygulama özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl ekleyebilirsiniz: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Çağrılı görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek ölçüm verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
