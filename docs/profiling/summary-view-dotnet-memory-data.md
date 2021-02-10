---
title: Özet görünümü-.NET bellek verileri | Microsoft Docs
description: Özet görünümünün, en fazla belleği ayrılan .NET işlevleri ve türleri hakkında bilgi görüntülemesini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6aa2daf8e03f61d529f0d07c8f78af49821fa92b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960019"
---
# <a name="summary-view---net-memory-data"></a>Özet görünümü-.NET bellek verileri
Özet görünümü, en fazla belleği alan .NET işlevleri ve türleri ve profil oluşturma çalıştırmasında en çok oluşturulan türleri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Zaman çizelgesi grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturma sırasında profili oluşturulan uygulamanın işlemci (CPU) kullanımını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Çoğu belleği ayıran işlevler
 Profil oluşturma çalıştırmasında en fazla bellek bayt sayısını ayrılan işlevleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Sayacının**|Bu işlev tarafından veya bu işlev tarafından çağrılan bir alt işlev tarafından ayrılan, profil oluşturma çalıştırmasında ayrılan tüm baytların yüzdesi.|

## <a name="types-with-most-memory-allocated"></a>En fazla bellek ayrılmış türler
 Profil oluşturma çalıştırmasında en fazla bellek bayt sayısı ayrıldığı türleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Türün adı.|
|**Sayacının**|Bu tür için ayrılan profil oluşturma çalıştırmasında ayrılan tüm baytların yüzdesi.|

## <a name="types-with-most-instances"></a>En çok örneği olan türler
 Profil oluşturma çalışması sırasında en fazla oluşturulan türleri listeler. sey

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Türün adı.|
|**Larında**|Bu türün örnekleri olan profil oluşturma çalıştırmasında oluşturulan toplam of.NET nesne sayısı yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü-örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü-izleme verileri](../profiling/summary-view-instrumentation-data.md)
