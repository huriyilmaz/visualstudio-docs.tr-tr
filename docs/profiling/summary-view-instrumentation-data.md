---
title: Özet görünümü-Izleme verileri | Microsoft Docs
description: Özet görünümünün en fazla performans maliyeti olan işlevlerle ilgili bilgileri ve bildirim bağlantılarının ve rapor listelerinin açıklamasını nasıl görüntülediğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c5d8579b68eeceed3843a8dd6a6fe71e9f9015c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141239"
---
# <a name="summary-view---instrumentation-data"></a>Özet görünümü-izleme verileri
Özet görünümü, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Zaman çizelgesi Graph
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturma sırasında profili oluşturulan uygulamanın işlemci (CPU) kullanımını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Etkin yol
 **Etkin yol** , en çok kullanılan yürütme yolunu görüntüler. İşlevin Işlev ayrıntıları görünümünü görüntülemek için bir işleve tıklayabilirsiniz. İşlevin diğer görünümlerini görüntülemek için, işlevine sağ tıklayın ve sonra listeden bir görünüme tıklayın.

 **Etkin yol** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Geçen kapsamlı süre yüzdesi**|İşlevin işlev gövdesinde ve çağrılan işlevlerde kod çalıştırırken harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi.|
|**Geçen dışlamalı süre yüzdesi**|İşlevin işlev gövdesinde kod yürütmeyi harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi. İşlevin çağrıldığı işlevlerde harcanan süre dahil değildir.|

## <a name="functions-with-most-individual-work"></a>En bireysel Işleri olan işlevler
 Çağrılan işlevlerde değil, işlevin gövdesinde kod yürütürken en çok kullanılan işlevlerin listesi.

 **En bireysel işleri olan işlevler** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Dışlamalı zaman yüzdesi**|İşlevin işlev gövdesinde kod yürütmeyi harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi. İşlevin çağrıldığı işlevlerde harcanan süre dahil değildir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü-örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü-.NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
