---
title: Özet Görünüm - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 649d0e9e5b32c124cfa962f45e4d128e4a32210f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778212"
---
# <a name="summary-view---sampling-data"></a>Özet Görünüm - örnekleme verileri
Özet görünümü, profil oluşturma çalışmasındaki en yüksek performans pahalı işlevler hakkındaki bilgileri görüntüler. Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için [Özet Görünüm](../profiling/summary-view.md)bölümüne bakın.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="timeline-graph"></a>Zaman Çizelgesi Grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın gerçekleştiği süre içinde profillenen uygulamanın işlemci (CPU) kullanım yüzdesini gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için [bkz: Özet Zaman Çizelgesi'nden rapor görünümlerini filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

## <a name="hot-path"></a>Sıcak Yol
 **Sıcak Yol,** çoğu örneğin toplandığı yürütme yolunu görüntüler. İşlevin İşlev Ayrıntıları görünümünü görüntülemek için bir işlevi tıklatabilirsiniz. İşlev için diğer görünümleri görüntülemek için işlevi sağ tıklatın ve ardından listeden bir görünüm e tıklayın.

 **Sıcak Yol** her işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin adı.|
|**Kapsayıcı Örnekler %**|Bu işlev veya bu işlev tarafından çağrılan bir işlev yürütüldüğünde oluşan tüm örneklerin yüzdesi.|
|**Özel Örnekler %**|İşlev işlevi gövdesinde kod yürütüldüğünde oluşan tüm örneklerin yüzdesi. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil edilmez.|

## <a name="functions-doing-most-individual-work"></a>En Bireysel İş Yapan Fonksiyonlar
 **En Çok Bireysel İş Yapan İşlevler,** profil oluşturma çalışmasında en çok sayıda özel örnek içeren işlevleri görüntüler. Örnek toplandığında işlev kendi kodunu çalıştırıyorsa, özel bir örnek bir işleve atanır. Örnek toplandığında işlev başka bir işlevi çağırıyorsa, özel bir örnek işleve atanmez. Çok sayıda özel örnek, işlevin kendisinde önemli bir zaman harcandıdığını gösterir.

 İşlevin İşlev Ayrıntıları görünümünü görüntülemek için bir işlevi tıklatabilirsiniz. İşlev için diğer görünümleri görüntülemek için işlevi sağ tıklatın ve ardından listeden bir görünüm e tıklayın.

 **En Çok Bireysel İş Yapan İşlevler** her işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|İşlevin adı.|
|**Özel Örnekler %**|İşlev işlevi işlevi gövdesinde kod yürütüldüğünde toplanan profil oluşturma çalışmasındaki tüm örneklerin yüzdesi. Bu işlev olarak adlandırılan işlevler yürütüldüğünde toplanan örnekleri yüzde hariç tutar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet Görünümü - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
- [Özet Görünüm - enstrümantasyon verileri](../profiling/summary-view-instrumentation-data.md)
