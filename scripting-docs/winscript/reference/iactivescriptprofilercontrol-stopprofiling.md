---
title: 'Iactivescriptprofilercontrol:: Stopprofilleme | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571543"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Komut dosyası altyapısında profil oluşturmayı durduruyor. Bu yöntem, profil oluşturucu nesnesinde [ıactivescriptprofilercallback:: kapatılmasını](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) çağırır ve sonra bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hrShutdownReason`  
 'ndaki Profil Oluşturucu nesnesinin [ıactivescriptprofilercallback:: kapanıyor](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) metoduna parametre olarak geçirilecek HRESULT.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerControl Arabirimi](../../winscript/reference/iactivescriptprofilercontrol-interface.md)