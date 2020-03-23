---
title: Özet Görünüm - Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2f52f80cad4ce7678a832a7b76a75d8f2fd4460e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778225"
---
# <a name="summary-view---instrumentation-data"></a>Özet görünüm - enstrümantasyon verileri
Özet görünümü, profil oluşturma çalışmasındaki en yüksek performans pahalı işlevler hakkındaki bilgileri görüntüler. Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için [Özet görünümüne](../profiling/summary-view.md)bakın.

## <a name="timeline-graph"></a>Zaman Çizelgesi Grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın gerçekleştiği süre içinde profillenen uygulama tarafından işlemci (CPU) kullanımını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için [bkz: Özet Zaman Çizelgesi'nden rapor görünümlerini filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

## <a name="hot-path"></a>Sıcak Yol
 **Sıcak Yol,** en çok tüketilen yürütme yolunu görüntüler. İşlevin İşlev Ayrıntıları görünümünü görüntülemek için bir işlevi tıklatabilirsiniz. İşlev için diğer görünümleri görüntülemek için işlevi sağ tıklatın ve ardından listeden bir görünüm e tıklayın.

 **Sıcak Yol** her işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin adı.|
|**Geçen Kapsayıcı Süre %**|Profil oluşturma verilerinde, işlevin işlev gövdesinde ve çağırdığı işlevlerde kodu yürütmek için harcadığı tüm zamanların yüzdesi.|
|**Geçen Özel Zaman %**|Profil oluşturma verilerindeki tüm zamanların yüzdesi, işlevin işlev gövdesinde kodu yürütmeye harcadığı dır. Çağrılan işlevin dahil olmadığı işlevlerde harcanan süre.|

## <a name="functions-with-most-individual-work"></a>Çoğu Bireysel Çalışmayla Fonksiyonlar
 Çağrılan işlevlerde değil, işlevin gövdesinde en çok zaman kod yürütmeyi tüketen işlevlerin listesi.

 **En Bireysel Çalışma ile işlevler** her işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin adı.|
|**Özel Zaman %**|Profil oluşturma verilerindeki tüm zamanların yüzdesi, işlevin işlev gövdesinde kodu yürütmeye harcadığı dır. Çağrılan işlevin dahil olmadığı işlevlerde harcanan süre.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünüm - örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünüm - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
