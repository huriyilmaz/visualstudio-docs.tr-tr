---
title: Fonksiyonlar Görünümü - .NET Bellek Enstrümantasyon Verileri | Microsoft Dokümanlar
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
ms.openlocfilehash: eba1f0d1434d253aaca698d3ae582e3c507c2d23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779239"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Fonksiyonlar Görünümü - .NET bellek enstrümantasyon verileri
Enstrümantasyon yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin İşlevler görünümü, profil oluşturma çalışması sırasında belleği ayıran işlevleri listeler. İşlev satırı, ayırmaların boyutunu ve sayısını ve işlevin zamanlama verilerini bildirir.

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
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Zaman Özel Sonda Genel**|Enstrümantasyon nedeniyle bu işlev için zaman yükü. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon nedeniyle alt fonksiyonları. Sonda yükü her şey dahil zamanlardan çıkarıldı.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmalarını) ve boyutunu (baytları) gösterir.

 Özel bellek değerleri, alt işlevleri tarafından değil, işlev tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Tahsisatlar**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde oluşturulan nesnelerin toplam sayısı.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Özel Tahsisler**|İşlev işlevi gövdesinde kod yürütüldüğünde oluşturulan nesnelerin toplam sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin özel ayırmalarıdır.|
|**Dahil Baytlar**|Bu işlevde ve bu işlev tarafından çağrılan işlevlerde ayrılan bellek baytlarının sayısı.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin kapsayıcı baytları olan tüm bellek baytlarının yüzdesi.|
|**Özel Baytlar**|Bu işlev tarafından ayrılan ancak bu işlev tarafından çağrılan işlevler tarafından değil, bellek baytlarının sayısı.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin münhasır baytları olan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Süre %**|Bu işlevin geçen kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Bu işleve yapılan bir çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Bu işleve yapılan bir çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Bu işleve yapılan bir çağrının minimum kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda geçen süreyi içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|Bu işleve yapılan tüm çağrıların toplam geçen özel süresi.|
|**Geçen Özel Zaman %**|Profil oluşturma çalışmasının, bu işlevin toplam geçen özel süresinde harcanan toplam geçen özel sürenin yüzdesi.|
|**Avg Geçen Özel Zaman**|Bu işlev için bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Bu işlev için bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Bu işlev için bir çağrının minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|Bu işleve yapılan tüm çağrıların toplam uygulama kapsayıcı süresi.|
|**Uygulama Kapsayıcı Süresi %**|Bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı ve alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|Bu fonksiyona yapılan tüm çağrıların toplam uygulama münhasır süresi.|
|**Uygulama Özel Zaman %**|Profil oluşturma çalışmasının, bu işlevin toplam uygulama münhasır süresinde harcanan toplam geçen münhasır sürenin yüzdesi.|
|**Avg Uygulama Özel Zaman**|Bu işlev için bir çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Bu işlev için bir çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Bu işlev için bir çağrının minimum uygulama münhasır süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Fonksiyonlar Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-instrumentation-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-sampling-data.md)
