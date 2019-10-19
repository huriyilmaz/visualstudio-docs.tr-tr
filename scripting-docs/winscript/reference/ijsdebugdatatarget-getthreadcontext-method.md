---
title: 'IJsDebugDataTarget:: GetThreadContext Yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577652"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext Yöntemi
Verilen iş parçacığının bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 'ndaki Hedef işlemde çalışan iş parçacığı.  
  
 `contextFlags`  
 'ndaki Bağlam bayraklarını belirtir. Bu, BAĞLAMı 'nın ContextFlags alanıyla aynı (daha fazla bilgi için bkz. Winnt. h, CONTEXT_ALL araması).  
  
 `contextSize`  
 'ndaki PContext tarafından belirtilen arabelleğin boyutu.  
  
 `pContext`  
 dışı Platforma özgü bağlam yapısını pContext tarafından belirtilen arabelleğe alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)