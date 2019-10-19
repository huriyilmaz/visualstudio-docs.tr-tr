---
title: 'Iactivescriptprofilercallback:: OnFunctionEnter | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571690"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Betik altyapısının Belge Nesne Modeli (DOM) çağrısı olmayan bir işlev çağrısını yürütmek üzere olduğunu profil oluşturucu nesnesine bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnFunctionEnter(  
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
 DOM çağrıları için, komut dosyası altyapısı `IActiveScriptProfilerCallback::OnFunctionEnter` yerine [ıactivescriptprofilercallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) öğesini çağırır. Bunun nedeni, DOM 'daki çok sayıda benzersiz Yöntem ve özelliklerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)    
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)