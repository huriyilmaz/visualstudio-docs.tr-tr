---
title: Çağrı ağacı görünümü-Izleme verileri | Microsoft Docs
description: Çağrı ağacı görünümünün, Performans Gezgini arama ağacındaki izleme bilgilerini görüntüleme hakkında bilgi edinin.
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
ms.openlocfilehash: 9757e38bc11f9a01f7d94625023aa59f4c593474
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084759"
---
# <a name="call-tree-view---instrumentation-data"></a>Çağrı ağacı görünümü-izleme verileri
Çağrı ağacındaki bir işlevin değerleri, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin süresini belirtir. Yüzde değerleri, işlev örneklerinin değeri, profil oluşturma çalıştırışında tüm işlevlerin toplam geçen dahil süresi ile karşılaştırılarak hesaplanır.

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
|**İşlem adı**|İşleme atanan ad.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev için, izleme nedeniyle oluşan zaman ek yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt işlevleri, izleme nedeniyle oluşur. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|
|**Düzeyde**|Çağrı ağacındaki işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlevin bu örneklerinin çağrı yığınında saati belirtir. Süre, işlev tarafından çağrılan alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılar için harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|Bu işlev için bu işleve yapılan çağrıların toplam geçen kapsamlı süresi.|
|**Geçen kapsamlı süre yüzdesi**|Bu bağlamda bu işlevin toplam geçen kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen maksimum kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, çağrı ağacındaki üst işlev tarafından çağrılan bir işlev örneklerinin işlev gövdesinde kod yürüttüğünü belirtir; diğer bir deyişle, işlev çağrı yığınının en üstünde olduğunda. Bu süre, işletim sistemine çağrı sırasında bağlam anahtarları ve giriş/çıkış işlemleri gibi zaman alır. Ancak, süre, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|Bu bağlamda bu işleve yapılan tüm çağrıların geçen toplam dışlamalı süresi.|
|**Geçen dışlamalı süre yüzdesi**|Bu bağlamda bu işlevin toplam geçen dışlamalı süre içinde harcanan toplam çalışma zamanında geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri, çağrı ağacındaki üst işlev tarafından çağrılan bir işlevin örneklerinin çağrı yığınında olduğunu gösterir. Bu süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez, ancak bu süre, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan tüm çağrıların Toplam uygulama kapsamlı süresi.|
|**Uygulama kapsamlı süresi%**|Bu bağlamda bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.|
|**En az uygulama kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulamanın dışlamalı değeri, çağrı ağacındaki üst işlev tarafından çağrılan bir işlev örneklerinin işlev gövdesinde doğrudan kod yürüttüğünü belirtir; diğer bir deyişle, işlev çağrı yığınının en üstünde olduğunda. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez. Ayrıca, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|Bu bağlamda bu işleve yapılan tüm çağrıların Toplam uygulama dışlamalı süresi.|
|**Uygulama dışlamalı süresi%**|Bu bağlamda bu işlevin toplam uygulama dışlamalı saatinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı ağacı görünümü-izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
