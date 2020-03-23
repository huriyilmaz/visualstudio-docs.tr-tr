---
title: İşlevler Görünümü - Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 423b6d61af93c37e6fa83549ed3fa5d422128165
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779226"
---
# <a name="functions-view---instrumentation-data"></a>İşlevler Görünümü - enstrümantasyon verileri
İşlevler raporu görünümü, profil oluşturma verilerini işlev adına göre listeler.

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
|**Zaman Özel Sonda Genel**|Enstrümantasyonun neden olduğu bu işlev için gereken süre. İşlev tarafından çağrılan işlevlerde ek yükü içermez. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon neden olduğu alt işlevleri. İşlev tarafından çağrılan işlevlerde genel merkez içerir. Sonda yükü her şey dahil zamanlardan çıkarıldı.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan işlev ve zaman tarafından çağrılan işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Süre %**|Bu işlevin geçen kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Bu işleve yapılan bir çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Bu işleve yapılan bir çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Bu işleve yapılan bir çağrının minimum kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin işlevin gövdesinde kodu yürütme sebebinde, yani işlevin çağrı yığınının en üstünde olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içerir, ancak işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|Bu işleve yapılan tüm çağrıların toplam geçen özel süresi.|
|**Geçen Özel Zaman %**|Profil oluşturma çalışmasının, bu işlevin toplam geçen özel süresinde harcanan toplam geçen özel sürenin yüzdesi.|
|**Avg Geçen Özel Zaman**|Bu işlev için bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Bu işlev için bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Bu işlev için bir çağrının minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, ancak işlev tarafından çağrılan işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|Bu işleve yapılan tüm çağrıların toplam uygulama kapsayıcı süresi.|
|**Uygulama Kapsayıcı Süresi %**|Bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Bu işleve yapılan bir çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez ve işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|Bu fonksiyona yapılan tüm çağrıların toplam uygulama münhasır süresi.|
|**Uygulama Özel Zaman %**|Profil oluşturma çalışmasının, bu işlevin toplam uygulama münhasır süresinde harcanan toplam geçen münhasır sürenin yüzdesi.|
|**Avg Uygulama Özel Zaman**|Bu işlev için bir çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Bu işlev için bir çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Bu işlev için bir çağrının minimum uygulama münhasır süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-sampling-data.md)
- [Fonksiyonlar Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Fonksiyonlar Görünümü - enstrümantasyon](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
