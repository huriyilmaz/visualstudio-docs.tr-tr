---
title: 'Iactivescriptprofilercallback:: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571674"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Profil Oluşturucu nesnesine, betik altyapısının Belge Nesne Modeli (DOM) çağrısı olmayan bir işlev çağrısını yürütmeyi tamamladığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `scriptId`  
 'ndaki İşlevin parçası olduğu betiğin benzersiz KIMLIĞI. Bu KIMLIK, komut dosyası altyapısı tarafından atanır.  
  
 `functionId`  
 'ndaki İşlevin benzersiz KIMLIĞI. Bu KIMLIK, komut dosyası altyapısı tarafından atanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 DOM çağrıları için, komut dosyası altyapısı `IActiveScriptProfilerCallback::OnFunctionExit` yerine [ıactivescriptprofilercallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) öğesini çağırır. Bunun nedeni, DOM 'daki çok sayıda benzersiz Yöntem ve özelliklerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)