---
title: Özet görünümü-örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c759922fcd28ce0b686745fc917c02f41762cae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817983"
---
# <a name="summary-view---sampling-data"></a>Özet Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özet görünümü, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Zaman çizelgesi grafiği  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özet görünümü](../profiling/summary-view-dotnet-memory-data.md)   
 [Özet Görünümü](../profiling/summary-view-instrumentation-data.md)
