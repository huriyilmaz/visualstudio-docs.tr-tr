---
title: Arayan-Callee Görünümü - Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 551c183dd9c368b1af16c1fe52b36762f4e71504
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773302"
---
# <a name="callercallee-view---instrumentation-data"></a>Arayan/Callee görünümü - enstrümantasyon verileri
Arayan/Callee görünümü, seçili bir işlev ve çağrı ağacında üst ve alt işlevleri hakkında profil oluşturma bilgilerini görüntüler. Arayan/Callee görünümü üç ızgara içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işlev hakkında profil oluşturma bilgilerini gösterir. Değerler, işleve yapılan tüm çağrıları içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst ızgarada görüntülenir ve seçili işlevin arayan (üst) işlevleri hakkında profil oluşturma bilgilerini gösterir. Değerler, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin değerini gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt ızgarada görüntülenir ve seçili işlevin callee (alt) işlevleri örnekleri hakkında profil oluşturma bilgilerini gösterir. Değerler, yalnızca geçerli işlev tarafından çağrıldığında alt işlevde harcanan zamanı gösterir.

## <a name="general"></a>Genel
 Genel sütunlar bir görünüm satırında işlevi tanımlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Fonksiyon Adı**|İşlevin adı.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan toplam arama sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Zaman Özel Sonda Genel**|Enstrümantasyon nedeniyle bu işlev için zaman yükü. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon neden olduğu alt işlevleri. Sonda yükü her şey dahil zamanlardan çıkarıldı.|
|**Tür**|Fonksiyonun bağlamı:<br /><br /> **0** - geçerli fonksiyon<br /><br /> **1** - geçerli işlevi çağıran bir işlev<br /><br /> **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Fonksiyon Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Geçerli işlev için, işlevde harcanan süre. Değer, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen kapsayıcı zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örneklerinde harcanan süre. Değer, callee'nin alt işlevlerinde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.|
|**Geçen Kapsayıcı Süre %**|Bu bağlamda, bu işlevin geçen kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|- Geçerli işlev için, işlevin doğrudan yürütülmesinde harcanan süre. Değer, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen özel zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örneklerinde harcanan süre. Değer, callee işlevinin alt işlevlerinde harcanan zamanı dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen Özel Zaman %**|Bu bağlamda, bu işlevin toplam geçen özel zamanında harcanan profil oluşturma çalışmasının toplam geçen özel zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|- Geçerli işlev için, işlev ve alt işlevleri harcanan zaman. Değer, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı dışlar.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin uygulama kapsayıcı zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örneklerinde harcanan süre. Değer, callee işlevinin alt işlevlerinde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez.|
|**Uygulama Kapsayıcı Süresi %**|Bu bağlamda bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresiyüzdesi.|
|**Avg Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri işlevde harcanan zamanı gösterir. Bu, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|- Geçerli işlev için, işlevin doğrudan yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen aramalar tarafından oluşturulan geçerli işlevin uygulama münhasır zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örneklerinde harcanan süre. Değer, callee işlevinin alt işlevlerinde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.|
|**Uygulama Özel Zaman %**|Bu bağlamda bu işlevin toplam uygulama münhasır süresi harcanan profil oluşturma çalışmasının toplam geçen özel zaman yüzdesi.|
|**Avg Uygulama Özel Zaman**|Bu bağlamda bu işleve bir çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum uygulama münhasır süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Callee görünümü - veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Callee görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
