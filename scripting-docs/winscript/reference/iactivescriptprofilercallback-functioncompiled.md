---
title: 'Iactivescriptprofilercallback:: Functionderlenen | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576471"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Profil Oluşturucu nesnesine betik derlenirken komut dosyası altyapısının bir işlevle karşılaştığı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki İşlevin benzersiz KIMLIĞI. Bu KIMLIK, komut dosyası altyapısı tarafından atanır.  
  
 `scriptId`  
 'ndaki İşlevin parçası olduğu betiğin benzersiz KIMLIĞI.  
  
 `pwszFunctionName`  
 'ndaki Bir anonim işlev için, işlevin adı veya null.  
  
 `pwszFunctionNameHint`  
 'ndaki İşlevin gösterilen adı veya betik altyapısı herhangi bir ad çıkarsanmezse null.  
  
 `pIDebugDocumentContext`  
 'ndaki Varsa, profil oluşturucunun bir [ıdebugdocumentcontext arabirimi](../../winscript/reference/idebugdocumentcontext-interface.md) işaretçisi için sorgulaması gereken `IUnknown` arabirimine yönelik işaretçi. Aksi takdirde, null.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı, yalnızca konak tarafından destekleniyorsa belge bağlamını sağlayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)