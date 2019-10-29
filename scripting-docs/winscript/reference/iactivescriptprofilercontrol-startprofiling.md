---
title: 'Iactivescriptprofilercontrol:: Startprofilleme | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b37b60f50351496faceb97190ae0d173eba3a5f4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983263"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Komut dosyası altyapısında profil oluşturmayı başlatır. Betik altyapısı, bir [Cocreateınstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)çağrısı yaparak Profiler nesnesinin bir örneğini oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `clsidProfilerObject`  
 'ndaki Oluşturulacak profil oluşturucu nesnesinin sınıf tanımlayıcısı (CLSID).  
  
 `dwEventMask`  
 'ndaki Olay türlerini belirten 4 baytlık bir bit maskesi. Bitleri [PROFILER_EVENT_MASK numaralandırması](../../winscript/reference/profiler-event-mask-enumeration.md)içinde tanımlanmıştır.  
  
 `dwContext`  
 'ndaki Profiler nesnesine geçirilen 4 baytlık bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profil oluşturma zaten etkin.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerControl Arabirimi](../../winscript/reference/iactivescriptprofilercontrol-interface.md)