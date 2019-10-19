---
title: 'Iactivescriptprofilercallback:: Scriptderlenen | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571668"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Profil Oluşturucu nesnesine komut dosyası altyapısının bir betik derlediğini bildirir. Bu yöntem, derlenen her komut dosyası için çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `scriptId`  
 'ndaki Derlenen betiğin benzersiz KIMLIĞI. Bu KIMLIK, komut dosyası altyapısı tarafından atanır.  
  
 `type`  
 'ndaki Derlenen betiğin türü. Değerler [PROFILER_SCRIPT_TYPE numaralandırması](../../winscript/reference/profiler-script-type-enumeration.md)içinde tanımlanır.  
  
 `pIDebugDocumentContext`  
 'ndaki Varsa, profil oluşturucunun bir [ıdebugdocumentcontext arabirimi](../../winscript/reference/idebugdocumentcontext-interface.md) işaretçisi için sorgulaması gereken `IUnknown` arabirimine yönelik bir işaretçi. Aksi takdirde, bu null olacaktır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı, yalnızca konak tarafından destekleniyorsa belge bağlamını sağlayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)