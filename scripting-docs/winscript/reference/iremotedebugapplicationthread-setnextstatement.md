---
title: 'Iremotedebugapplicationthread:: Setnextdeyimin | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575516"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Verilen çerçeve bağlamında, belirtilen kod bağlamına olabildiğince yakın devam etmek için yürütmeyi zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStackFrame`  
 'ndaki Yığın çerçeve nesnesi. Bu bağımsız değişken NULL olabilir, bu da geçerli yığın çerçevesinin kullanılması gerektiğini gösterir.  
  
 `pCodeContext`  
 'ndaki Kod bağlamı. Bu bağımsız değişken NULL olabilir, bu, geçerli kod bağlamını kullanılması gerektiğini gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `pStackFrame` tarafından belirtilen çerçeve bağlamında `pCodeContext` tarafından belirtilen kod bağlamına olabildiğince yakın şekilde devam etmek için yürütmeyi zorlar. Bu bağımsız değişkenlerden herhangi biri, geçerli çerçeveyi veya bağlamı temsil eden `NULL` olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplicationThread Arabirimi](../../winscript/reference/iremotedebugapplicationthread-interface.md)