---
title: marker_series sınıfı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194939"
---
# <a name="marker_series-class"></a>marker_series Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-constructors"></a>Ortak Oluşturucular  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[marker_series::marker_series Oluşturucusu](../profiling/marker-series-marker-series-constructor.md)|`marker_series` sınıfının yeni bir örneğini başlatır.|  
|[marker_series::~marker_series Yok Edicisi](../profiling/marker-series-tilde-marker-series-destructor.md)|Marker_series nesnesini yok eder ve tüm ayrılmış kaynakları serbest bırakır.|  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[marker_series::is_enabled Yöntemi](../profiling/marker-series-is-enabled-method.md)|Sağlayıcının herhangi bir oturumun etkinleştirilip etkinleştirilmediğini belirler.|  
|[marker_series::write_alert Yöntemi](../profiling/marker-series-write-alert-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir uyarı yazar.|  
|[marker_series::write_flag Yöntemi](../profiling/marker-series-write-flag-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir bayrak yazar.|  
|[marker_series::write_message Yöntemi](../profiling/marker-series-write-message-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir ileti yazar.|  
  
## <a name="inheritance-hierarchy"></a>Devralma Hiyerarşisi  
 `marker_series`  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvmarkersobj. h  
  
 **Ad alanı:** Eşzamanlılık::d ıagstik  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama ad alanı](../profiling/diagnostic-namespace.md)
