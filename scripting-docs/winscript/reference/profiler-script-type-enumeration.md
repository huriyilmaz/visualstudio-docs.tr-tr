---
title: PROFILER_SCRIPT_TYPE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574579"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE Numaralandırması
Betiğin türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Kullanıcı tarafından yazılmış betik kodunu belirtir.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Yürütme sırasında dinamik olarak oluşturulan betik kodunu belirtir.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Komut dosyası altyapısı tarafından tanımlanan yerel işlevler ve nesneler için komut dosyası türünü belirtir.|  
|PROFILER_SCRIPT_TYPE_DOM|Internet Explorer 'ın Belge Nesne Modeli (DOM) çağrısı (örneğin, `document.getElementById` yöntemine bir çağrı) belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin komut dosyası profil oluşturucu sabitleri, numaralandırmalar ve yapılar](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [Iactivescriptprofilercallback:: Scriptderlenen](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [Iactivescriptprofilercallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)