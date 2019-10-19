---
title: 'Iactivescriptprofilercontrol:: SetProfilerEventMask | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571585"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Betik altyapısının yükseltecağı olay türlerini belirten 4 baytlık bir bit maskesi ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwEventMask`  
 'ndaki Olay türlerini belirten 4 baytlık bir bit maskesi. Bitleri [PROFILER_EVENT_MASK numaralandırması](../../winscript/reference/profiler-event-mask-enumeration.md)içinde tanımlanmıştır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerControl Arabirimi](../../winscript/reference/iactivescriptprofilercontrol-interface.md)