---
title: Arayan-Callee Görünümü - NET Bellek Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c51f4bc1e823f565670bf1f6df77553ff4658d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779733"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri
.NET bellek profil oluşturma verilerinin Arayan/Callee görünümü, enstrümantasyon yöntemi kullanılarak toplanan seçili bir işlev için ayırma ve zamanlama verilerini ve seçilen işlevin üst ve alt işlevlerini görüntüler. Arayan/Callee görünümü üç ızgara içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işlev hakkında bellek profil oluşturma bilgilerini gösterir. Değerler, işleve örneklenmiş tüm çağrıları içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst kılavuzda görüntülenir ve arayan (üst) işlevinden gelen çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerini gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin callee (alt) işlevleri için bellek profil oluşturma verilerini gösterir.

 Bu satırı geçerli işlev yapmak için bir arayanın veya callee işlev satırına çift tıklayın.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**Fonksiyon Adı**|İşlevin adı.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan toplam arama sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği.|
|**İşlem Adı**|İşleme atanan ad.|
|**Zaman Özel Sonda Genel**|Enstrümantasyon nedeniyle bu işlev için zaman yükü. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon nedeniyle alt fonksiyonları. Sonda yükü her şey dahil zamanlardan çıkarıldı.|
|**Tür**|Fonksiyonun bağlamı:<br /><br /> **0** - geçerli fonksiyon<br /><br /> **1** - geçerli işlevi çağıran bir işlev<br /><br /> **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Fonksiyon Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Tahsisler**|- Geçerli işlev için, işlev işlev gövdesinde kod yürütüldüğünde oluşturulan nesnelerin sayısı (diğer bir deyişle, işlev çağrı yığınının en üstündeyken). Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin özel ayırmalarının sayısı.<br />- Bir callee işlevi için, geçerli işlev tarafından çağrılan bu işlevin örnekleri tarafından oluşturulan nesnelerin sayısı. Bu sayı, callee işlevi tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin özel ayırmalarıdır.|
|**Kapsayıcı Tahsisatlar**|- Geçerli işlev için, profil oluşturma çalışmasında işlev tarafından ayrılan nesnelerin sayısı. Sayı, işlev tarafından çağrılan callee işlevlerinde oluşturulan nesneleri içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin kapsayıcı ayırmalarının sayısı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Sayı, bu callee işlevi tarafından çağrılan işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Özel Baytlar**|- Geçerli işlev için, profil oluşturma çalışmasındaki işlev tarafından ayrılan bellek baytlarının sayısı. Sayı, işlev tarafından çağrılan callee işlevlerine ayrılan belleği içermez.<br />- Bir arayan işlevi için, bu arayan işlevi tarafından yapılan çağrılardan oluşturulan geçerli işlevin özel baytlarının sayısı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, callee işlevi tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin özel ayırmaları olan tüm bellek baytlarının yüzdesi.|
|**Dahil Baytlar**|- Geçerli işlev için, profil oluşturma çalışmasındaki işlev tarafından ayrılan bellekteki bayt sayısı. Sayı, işlev tarafından çağrılan callee işlevlerinde ayrılan belleği içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevörneklerinin kapsayıcı bayt sayısı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, bu callee işlevi tarafından çağrılan işlevler tarafından ayrılan baytları içerir.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Geçerli işlev için, işlevde harcanan süre. Değer, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen kapsayıcı zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevde harcanan süre. Değer, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.|
|**Geçen Kapsayıcı Süre %**|Bu bağlamda, bu işlevin geçen kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda geçen süreyi içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|- Geçerli işlev için, işlevin gövdesinin yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin geçen özel zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevde harcanan süre. Değer, callee işlevinin alt işlevlerinde harcanan zamanı dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen Özel Zaman %**|Bu bağlamda, bu işlevin toplam geçen özel zamanında harcanan profil oluşturma çalışmasının toplam geçen özel zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|- Geçerli işlev için, işlev ve alt işlevleri harcanan zaman. Değer, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı dışlar.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen çağrılar tarafından oluşturulan geçerli işlevin uygulama kapsayıcı zaman miktarı.<br />- Bir callee işlevi için, bu işlevde harcanan süre ve geçerli işlevden gelen çağrılar tarafından oluşturulan alt işlevleri. Değer, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez.|
|**Uygulama Kapsayıcı Süresi %**|Bu bağlamda bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresiyüzdesi.|
|**Avg Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, alt işlevlerde harcanan süre hariç, işlevde harcanan zamanı gösterir. Belirtilen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları n için harcanan zamanı da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|- Geçerli işlev için, işlevin gövdesinin yürütülmesinde harcanan süre. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.<br />- Bir arayan işlevi için, bu arayan işlevinden gelen aramalar tarafından oluşturulan geçerli işlevin uygulama münhasır zaman miktarı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevde harcanan süre. Değer, callee işlevinin alt işlevlerinde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içermez.|
|**Uygulama Özel Zaman %**|Bu bağlamda bu işlevin toplam uygulama münhasır süresi harcanan profil oluşturma çalışmasının toplam geçen özel zaman yüzdesi.|
|**Avg Uygulama Özel Zaman**|Bu bağlamda bu işleve bir çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum uygulama münhasır süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Callee görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Callee görünümü - enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Arayan/Callee görünümü - veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)
