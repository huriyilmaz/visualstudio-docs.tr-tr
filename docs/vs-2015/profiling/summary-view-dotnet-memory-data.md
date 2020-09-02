---
title: Özet görünümü-.NET bellek verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe6d3982828d1e2a8ae4aeaba3d89b1b75f4f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193326"
---
# <a name="summary-view---net-memory-data"></a>Özet görünümü-.NET bellek verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özet görünümü](../profiling/summary-view-sampling-data.md)   
 [Özet Görünümü](../profiling/summary-view-instrumentation-data.md)
