---
title: Caller-Callee Görünümü - Ölçüm verisi | Microsoft Docs
description: Çağıran/Çağrılı görünümünün, çağrı ağacında ölçüm ölçüm bilgilerini nasıl görüntüleye Performans Gezgini.
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
ms.openlocfilehash: 08de14aa1c7616cbafcca8841a2c5d0400b97965
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076925"
---
# <a name="callercallee-view---instrumentation-data"></a>Arayan/Çağrılı görünümü - ölçüm verileri
Çağıran/Çağrılı görünümü, çağrı ağacında seçili bir işlev ve onun üst ve alt işlevleri hakkında profil oluşturma bilgilerini görüntüler. Çağıran/Çağrılı görünümü üç kılavuz içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçilen işlevle ilgili profil oluşturma bilgilerini gösterir. Değerler işleve yapılan tüm çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve seçilen işlevin çağıran (üst) işlevleri hakkında profil oluşturma bilgilerini gösterir. Değerler, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından çağrılan** işlevler alt kılavuzda görüntülenir ve seçilen işlevin çağrılır (alt) işlevlerinin örnekleri hakkında profil oluşturma bilgilerini gösterir. Değerler yalnızca geçerli işlev tarafından çağrıldıklarında alt işlevde harcanan zamanı gösterir.

## <a name="general"></a>Genel
 Genel sütunlar, bir görünüm satırı içinde işlevini tanımladı.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev Adı**|İşlevin adı.|
|**İşlev Adresi**|İşlevin adresi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Zaman Özel Yoklama Ek Yükü**|Bu işlev için ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm dışlama zamanlarından çıkarıldı.|
|**Zaman Dahil Yoklama Ek Yükü**|Bu işlev ve alt işlevleri için, ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm kapsayıcı zamanlardan çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> **0** - geçerli işlev<br /><br /> **1** - geçerli işlevi çağıran bir işlev<br /><br /> **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök İşlev Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Geçerli işlev için işlevde harcanan süre. değeri, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen kapsayıcı süresi miktarı.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örneklerde harcanan süre. değeri, çağrılının alt işlevlerine ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.|
|**Geçen Kapsayıcı Saat %**|Bu bağlamda bu işlevin geçen kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en az kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülmektedir zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı dahil değildir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|- Geçerli işlev için, işlevin doğrudan yürütülmesinde harcanan süre. değeri, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen özel süresi miktarı.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örneklerde harcanan süre. değeri, çağrılan işlevinin alt işlevlerinde harcanan zamanı dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen Özel Saat %**|Bu bağlamda bu işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**En Fazla Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun özel süresi.|
|**En Az Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en düşük özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|- Geçerli işlev için, işlevde ve onun alt işlevlerinde harcanan süre. değeri, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dışlar.<br />- Bir çağıranın işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin uygulama dahil süresi.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örneklerde harcanan süre. değeri çağrılı işlevinin alt işlevlerine harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir.|
|**Uygulama Dahil Saati %**|Bu bağlamda bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, işlevde harcanan zamanı gösterir. Bu, alt işlevlerde harcanan zamanı dışlar ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|- Geçerli işlev için, işlevin doğrudan yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.<br />- Çağıran işlevi için, bu çağıranın işlevinden yapılan çağrılar tarafından oluşturulan geçerli işlevin uygulamanın özel süresi.<br />- Bir çağrılı işlev için, geçerli işlevden yapılan çağrılar tarafından oluşturulan bu işlevin örneklerde harcanan süre. Değer, çağrıyı çağıran işlevinin alt işlevlerine harcanan zamanı veya bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.|
|**Uygulamaya Özel Saat %**|Bu bağlamda, bu işlevin toplam uygulama özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Çağrılı görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek ölçüm verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
