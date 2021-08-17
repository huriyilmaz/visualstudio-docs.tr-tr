---
title: Çağrı Ağacı Görünümü - Ölçüm verisi | Microsoft Docs
description: Çağrı Ağacı görünümünün, çağrı ağacında ölçüm bilgilerini nasıl görüntüleye Performans Gezgini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cbab3e863feba8ed2490a38f21923dcdce0531b19ee5d55b181d8b4ed38c447e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333788"
---
# <a name="call-tree-view---instrumentation-data"></a>Çağrı Ağacı görünümü - ölçüm verileri
Çağrı ağacında bir işlevin değerleri, çağrı ağacında üst işlev tarafından çağrılmış işlev örnekleri için saati gösterir. Yüzde değerleri, işlev örneklerinin değeri profil oluşturma çalıştırması içinde tüm işlevlerin geçen toplam kapsayıcı süresiyle karşılaştırarak hesaplanır.

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
|**İşlem Adı**|İşleme atanan ad.|
|**Zaman Özel Yoklama Ek Yükü**|Bu işlev için ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm dışlama zamanlarından çıkarıldı.|
|**Zaman Dahil Yoklama Ek Yükü**|Bu işlev ve alt işlevleri için, ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm kapsayıcı zamanlardan çıkarıldı.|
|**Düzey**|Çağrı ağacında işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, işlev örneklerinin çağrı yığınında, çağrı ağacında üst işlev tarafından çağrılmış olan zamanı gösterir. Bu süre, işlev tarafından çağrılan alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Saat %**|Bu bağlamda bu işlevin geçen toplam kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en az kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, çağrı ağacındaki üst işlev tarafından çağrılmış bir işlevin örneklerinin işlev gövdesinde kod yürütme zamanı olduğunu gösterir; diğer bir ifadeyle işlevin çağrı yığınının en üstünde olduğu zaman. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda zaman içerir. Ancak süre, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam özel süresi.|
|**Geçen Özel Saat %**|Bu bağlamda bu işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**En Fazla Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en uzun özel süresi.|
|**En Az Geçen Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının geçen en düşük özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, çağrı ağacında üst işlev tarafından çağrılmış bir işlevin örneklerinin çağrı yığınında olduğu zamanı gösterir. Süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, Ancak, süre işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam uygulama dahil süresi.|
|**Uygulama Dahil Saati %**|Bu bağlamda bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama dahil süresi.|
|**En Az Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulama özel değerleri, çağrı ağacında üst işlev tarafından çağrılmış bir işlevin örneklerinin işlev gövdesinde doğrudan kod yürütme zamanı olduğunu gösterir; diğer bir ifadeyle işlevin çağrı yığınının en üstünde olduğu zaman. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir. Ayrıca işlev tarafından çağrılan alt işlevlerde harcanan zamanı da içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam uygulama özel süresi.|
|**Uygulamaya Özel Saat %**|Bu bağlamda, bu işlevin toplam uygulama özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu bağlamda bu işleve yapılan bir çağrının en düşük uygulama özel süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı ağacı görünümü-izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
