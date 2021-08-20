---
title: Özet Görünümü - .NET Bellek Verileri | Microsoft Docs
description: Özet görünümünün en fazla bellek ayrılan .NET işlevleri ve türleri hakkında nasıl bilgi görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: b5c63a0133e8883d4626e78805b86299cfbee3f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141226"
---
# <a name="summary-view---net-memory-data"></a>Özet görünümü - .NET bellek verileri
Özet görünümü, en fazla bellek ayrılan .NET işlevleri ve türleri ve profil oluşturma çalıştırması içinde en çok oluşturulan türler hakkında bilgi görüntüler. Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için bkz. [Özet görünümü.](../profiling/summary-view.md)

## <a name="timeline-graph"></a>Zaman çizelgesi Graph
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın meydana geldiği zaman içinde profili profili yapılan uygulamanın işlemci (CPU) kullanımını gösterir. Zaman çizelgesi grafiğini kullanarak görünümü seçilen bir zaman aralığına göre filtre görebilirsiniz. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Özet Zaman Çizelgesi'nde rapor görünümlerini filtreleme.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

## <a name="functions-allocating-most-memory"></a>En Fazla Bellek Alan İşlevler
 Profil oluşturma çalıştırması içinde en fazla bayt bellek ayrılan işlevleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Bayt %**|Profil oluşturma çalıştırması içinde bu işlev veya bu işlev tarafından çağrılan bir alt işlev tarafından ayrılan tüm ayrılan baytların yüzdesi.|

## <a name="types-with-most-memory-allocated"></a>En Fazla Bellek Ayrılan Türler
 Profil oluşturma çalıştırması içinde en fazla bayt bellek ayrılan türleri listeler.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Türün adı.|
|**Bayt %**|Profil oluşturma çalıştırması içinde bu tür için ayrılan tüm ayrılan baytların yüzdesi.|

## <a name="types-with-most-instances"></a>Çoğu Örneği Olan Türler
 Profil oluşturma çalıştırması sırasında en çok oluşturulan türleri listeler. Hda

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Türün adı.|
|**Örnek %**|Profil oluşturma çalıştırması of.NET bu türün örnekleri olan nesnelerin toplam sayısının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü - örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü - ölçüm verileri](../profiling/summary-view-instrumentation-data.md)
