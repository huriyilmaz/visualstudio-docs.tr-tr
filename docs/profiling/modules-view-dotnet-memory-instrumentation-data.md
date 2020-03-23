---
title: Modülgörünümü - .NET Bellek Enstrümantasyon Verileri | Microsoft Dokümanlar
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
ms.openlocfilehash: 521c884a0a25d7fa975a4039e6ec3e36ff4dc020
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778550"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modülgörünümü - .NET bellek enstrümantasyon verileri
Enstrümantasyon yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin modülgörünümü, profil oluşturma çalışmasında yürütülen modüller tarafından bellek ve zamanlama verilerini gruplandırır. Modülün işlevleri için profil oluşturma verileri modül düğümünün altında listelenir.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin veya modülün adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işlev veya modüle yapılan toplam arama sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Modülün veya işlevin yürütüldettiği işlemin adı.|
|**Zaman Özel Sonda Genel**|Enstrümantasyon nedeniyle bu işlev veya modül için zaman yükü.|
|**Zaman Dahil Prob Genel**|Bu işlev veya modül için zaman yükü ve enstrümantasyon nedeniyle alt fonksiyonları.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve alt işlevleri tarafından oluşturulan nesnelerin sayısını (ayırmalarını) ve boyutunu (baytları) gösterir.

 Özel bellek değerleri, alt işlevleri tarafından değil, işlev tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir.

 Bir modülün kapsayıcı ve özel bellek değerleri, modüldeki işlevlerin kapsayıcı ve özel bellek değerlerinin toplamıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Tahsisatlar**|- Bir işlev için, işlev tarafından oluşturulan nesnelerin toplam sayısı. Bu sayı, işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içerir.<br />- Bir modül için, modülden en az bir işlev yürütüldüğünde ayrılan profil oluşturma çalışmasındaki nesne sayısı. Bu sayı, modül işlevlerinden gelen çağrılar tarafından oluşturulan işlevlerde ayrılan nesneleri içerir.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, modülün veya işlevin kapsayıcı ayırmalarıdır.|
|**Özel Tahsisler**|- Bir işlev için, işlev işlev gövdesinde kod yürütüldüğünde oluşturulan nesnelerin sayısı (diğer bir deyişle, işlev çağrı yığınının en üstündeyken). Bu sayı, işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir modül için, modüldeki fonksiyonların münhasır tahsisatlarının toplamı.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, modülün veya işlevin özel tahsisleridir.|
|**Özel Baytlar**|- Bir işlev için, işlev işlev gövdesindeki kodu yürütürken ayrılan belleğin toplam sayısı (diğer bir deyişle, işlev çağrı yığınının en üstündeyken). Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />- Bir modül için, modüldeki fonksiyonlar tarafından ayrılan münhasır baytların toplamı.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve modül, işlev, çizgi veya yönergeye özel baytlar olarak ayrılan tüm baytların yüzdesi.|
|**Dahil Baytlar**|- Bir işlev için, işlev tarafından ayrılan bayt sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />- Bir modül için, modülden en az bir işlev yürütüldüğünde ayrılan profil oluşturma çalışmasında ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve modül veya işlevin dahil baytlarını içeren tüm baytların yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|- Bir işlev için, işlevde harcanan süre. Bu, alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.<br />- Bir modül için, modüldeki en az bir fonksiyonun çağrı yığınında olduğu süre.|
|**Geçen Kapsayıcı Süre %**|Bu modülün veya işlevin toplam geçen kapsayıcı süresi nde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|- Bir işlev için, bu işleve çağrının ortalama kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|- Bir işlev için, bu işleve yapılan bir çağrının maksimum geçen kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum geçen kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum dahil süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda geçen süreyi içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|- Bir fonksiyon için, modül veya fonksiyonda harcanan süre. Bu, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir, ancak alt işlevlerde harcanan süreyi hariç tutar.<br />- Bir modül için, modüldeki fonksiyonların geçen özel sürelerinin toplamı.|
|**Geçen Özel Zaman %**|Bu modülün veya işlevin toplam geçen özel süresinde harcanan profil oluşturma çalışmasının toplam geçen münhasır zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|- Bir işlev için, bu işleve yapılan bir çağrının ortalama geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|- Bir işlev için, bu işlev için bir çağrının en fazla geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum geçen özel süresi.|
|**Min Geçen Özel Zaman**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|- Bir işlev için, işlev çağrıları harcanan zaman. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları hariç tutar.<br />- Bir modül için, işletim sistemine yapılan aramalarda harcanan süre hariç olmak üzere, modüldeki en az bir fonksiyonun çağrı yığınında olduğu süre.|
|**Uygulama Kapsayıcı Süresi %**|Bu modülün veya işlevin uygulama kapsayıcı süresinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Uygulama Dahil Süresi**|- Bir işlev için, bu işleve bir çağrının ortalama uygulama kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|- Bir işlev için, bu işleve bir çağrının maksimum uygulama kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum uygulama kapsayıcı zaman.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, alt işlevlerde harcanan süre hariç, modülveya işlevde harcanan zamanı gösterir. Belirtilen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|- Bir işlev için, bu fonksiyona yapılan çağrıların toplam uygulama münhasır süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların toplam uygulama münhasır süresi.|
|**Uygulama Özel Zaman %**|Bu modülün veya işlevin uygulama özel süresi içinde harcanan profil oluşturma çalışmasının toplam geçen münhasır zamanının yüzdesi.|
|**Avg Uygulama Özel Zaman**|- Bir işlev için, bu işleve bir çağrının ortalama uygulama özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama uygulama özel süresi.|
|**Max Uygulama Özel Zaman**|- Bir işlev için, bu işlev için bir çağrının maksimum uygulama münhasır süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum uygulama özel süresi.|
|**Min Uygulama Özel Zaman**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum uygulama özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modülgörünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
