---
title: Özet Görünüm - .NET Bellek Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a67902af99eaee6c75f92f86c2481dfc2afd744e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771562"
---
# <a name="summary-view---net-memory-data"></a>Özet görünüm - .NET bellek verileri
Özet görünümü, .NET işlevleri ve en çok belleği ayıran türleri ve profil oluşturma çalışmasında en çok oluşturulan türler hakkındaki bilgileri görüntüler. Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için [Özet görünümüne](../profiling/summary-view.md)bakın.

## <a name="timeline-graph"></a>Zaman Çizelgesi Grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın gerçekleştiği süre içinde profillenen uygulama tarafından işlemci (CPU) kullanımını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için [bkz: Özet Zaman Çizelgesi'nden rapor görünümlerini filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

## <a name="functions-allocating-most-memory"></a>Çoğu Belleği Ayıran Fonksiyonlar
 Profil oluşturma çalışmasında en çok sayıda bellek ayıran işlevleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin adı.|
|**Bayt %**|Profil oluşturma çalışmasında bu işlev veya bu işlev tarafından çağrılan bir alt işlev tarafından ayrılan tüm baytların yüzdesi.|

## <a name="types-with-most-memory-allocated"></a>En Çok Bellek Ayrılan Türleri
 Profil oluşturma çalışmasında en fazla sayıda bellek ayrıltının bulunduğu türleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Türün adı.|
|**Bayt %**|Bu tür için ayrılan profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|

## <a name="types-with-most-instances"></a>Çoğu Örneği Içeren Türler
 Profil oluşturma çalışması sırasında en çok oluşturulan türleri listeler. Hda

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Türün adı.|
|**Örnekler %**|Profil oluşturma çalışmasında oluşturulan of.NET bu tür örneklerden oluşan toplam sayı of.NET nesnelerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünüm - örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünüm - enstrümantasyon verileri](../profiling/summary-view-instrumentation-data.md)
