---
title: Özet görünümü-örnekleme verileri | Microsoft Docs
description: Özet görünümünün, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri nasıl görüntülediğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 14e97957951052322be67861c43e97c537c10cb42f15d8dbdc84172c0e1a4163
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121354013"
---
# <a name="summary-view---sampling-data"></a>Özet görünümü-örnekleme verileri
Özet görünümü, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="timeline-graph"></a>Zaman çizelgesi Graph
 Özet görünümündeki zaman çizelgesi grafiğinde profil oluşturma işleminin gerçekleştiği zaman içindeki profili oluşturulan uygulamanın işlemci (CPU) kullanımının yüzdesi gösterilir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Etkin yol
 **Etkin yol** , en çok örnek toplandığı yürütme yolunu görüntüler. İşlevin Işlev ayrıntıları görünümünü görüntülemek için bir işleve tıklayabilirsiniz. İşlevin diğer görünümlerini görüntülemek için, işlevine sağ tıklayın ve sonra listeden bir görünüme tıklayın.

 **Etkin yol** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Kapsamlı örnekler%**|Bu işlev veya bu işlev tarafından çağrılan bir işlev çalıştırıldığında oluşan tüm örneklerin yüzdesi.|
|**Dışlamalı örnekler%**|İşlev gövdesinde kod yürütürken oluşan tüm örneklerin yüzdesi. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil değildir.|

## <a name="functions-doing-most-individual-work"></a>En bireysel Işleri yapan işlevler
 **En çok bireysel çalışma listesini yapan işlevler** , profil oluşturma çalıştırmasında en fazla sayıda dışlamalı örnek içeren işlevleri görüntüler. Örnek toplandığında işlev kendi kodunu yürütülerek bir işleve özel bir örnek atanır. İşlev, örnek toplandığında başka bir işlevi arıyorsa, işleve özel bir örnek atanmaz. Çok sayıda dışlamalı örnek, işlevin kendisinde önemli bir zamanın harcandığını gösterir.

 İşlevin Işlev ayrıntıları görünümünü görüntülemek için bir işleve tıklayabilirsiniz. İşlevin diğer görünümlerini görüntülemek için, işlevine sağ tıklayın ve sonra listeden bir görünüme tıklayın.

 Her bir **Iş yapan işlevler** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Dışlamalı örnekler%**|İşlev gövdesinde kod yürütürken toplanan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi. Yüzde, bu işlevin çağrıldığı işlevler yürütüldüğü zaman toplanan örnekleri dışlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet Görünümü - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
- [Özet görünümü-izleme verileri](../profiling/summary-view-instrumentation-data.md)
