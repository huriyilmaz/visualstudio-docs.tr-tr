---
title: Özet görünümü-Izleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc0b4195d33a7bf72d17681b6d71e78f1bacfe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157773"
---
# <a name="summary-view---instrumentation-data"></a>Özet Görünümü - İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özet görünümü, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Zaman çizelgesi grafiği  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özet görünümü](../profiling/summary-view-sampling-data.md)   
 [Özet Görünümü](../profiling/summary-view-dotnet-memory-data.md)
