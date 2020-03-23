---
title: Modülgörünümü - Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6449ad30edf11d3d315532cc33db2a79c14f90b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778537"
---
# <a name="modules-view---instrumentation-data"></a>Modülgörünümü - enstrümantasyon verileri
Modüller görünümü, profil oluşturma verilerinde bulunan modüllere göre gruplanan performans verilerini görüntüler. Modülün işlevleri modül düğümünün altında listelenmiştir.

## <a name="general"></a>Genel
 Genel sütunlar bir görünüm satırında işlevi tanımlar.

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
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|- Bir fonksiyon için, modül veya fonksiyonda harcanan süre. Bu, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir, ancak alt işlevlerde harcanan süreyi hariç tutar.<br />- Bir modül için, modüldeki fonksiyonların geçen özel sürelerinin toplamı.|
|**Geçen Özel Zaman %**|Bu modülün veya işlevin toplam geçen özel süresinde harcanan profil oluşturma çalışmasının toplam geçen münhasır zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|- Bir işlev için, bu işleve yapılan bir çağrının ortalama geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|- Bir işlev için, bu işlev için bir çağrının en fazla geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum geçen özel süresi.|
|**Min Geçen Özel Zaman**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum geçen özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez. Ancak, zaman çocuk işlevleri harcanan zaman içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|- Bir işlev için, işlev çağrıları harcanan zaman. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları hariç tutar.<br />- Bir modül için, modüldeki en az bir fonksiyonun çağrı yığınında olduğu süre. Bu, işletim sistemine yapılan aramalarda harcanan zamanı hariç tutar.|
|**Uygulama Kapsayıcı Süresi %**|Bu modülün veya işlevin uygulama kapsayıcı süresinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Uygulama Dahil Süresi**|- Bir işlev için, bu işleve bir çağrının ortalama uygulama kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|- Bir işlev için, bu işleve bir çağrının maksimum uygulama kapsayıcı süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum uygulama kapsayıcı zaman.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri modül veya işlevde harcanan zamanı gösterir. Bu, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|Bu modül veya fonksiyon için tüm çağrıların toplam uygulama münhasır zaman.|
|**Uygulama Özel Zaman %**|Bu modülün veya işlevin uygulama özel süresi içinde harcanan profil oluşturma çalışmasının toplam geçen münhasır zamanının yüzdesi.|
|**Avg Uygulama Özel Zaman**|- Bir işlev için, bu işleve bir çağrının ortalama uygulama özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların ortalama uygulama özel süresi.|
|**Max Uygulama Özel Zaman**|- Bir işlev için, bu işlev için bir çağrının maksimum uygulama münhasır süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların maksimum uygulama özel süresi.|
|**Min Uygulama Özel Zaman**|- Bir fonksiyon için, bu modül veya fonksiyon için bir çağrının minimum uygulama özel süresi.<br />- Bir modül için, modüldeki fonksiyonlara yapılan tüm çağrıların minimum uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
- [Modülgörünümü - enstrümantasyon](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modülgörünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
