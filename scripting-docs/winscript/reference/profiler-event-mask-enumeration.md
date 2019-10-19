---
title: PROFILER_EVENT_MASK numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572286"
---
# <a name="profiler_event_mask-enumeration"></a>PROFILER_EVENT_MASK Numaralandırması
Profili oluşturulacak olay türlerini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Kullanıcı tarafından yazılan betikte ve dinamik kodda tanımlanan profiller işlevleri.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Komut dosyası altyapısı tarafından tanımlanan profiller yerel işlevleri.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Tüm Kullanıcı tanımlı ve betik altyapısı işlevleri, Belge Nesne Modeli çağrılar hariç (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|DOM 'a çağıran profiller işlevleri.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|DOM 'a çağrılar da dahil olmak üzere tüm işlevleri profiller.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin komut dosyası profil oluşturucu sabitleri, numaralandırmalar ve yapılar](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [Iactivescriptprofilercontrol:: SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)