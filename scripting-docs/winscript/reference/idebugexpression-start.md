---
title: 'Idebugexpression:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576438"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
İfadenin değerlendirmesini başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdecb`  
 'ndaki İfade değerlendirmesinin ne zaman tamamlandığını belirten geri çağırma. Bu parametre `NULL`, hiçbir olay tetiklenerek istemci, `QueryIsComplete` kullanarak ifade durumunu yoklamalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ifadenin değerlendirmesini başlatır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugexpression:: Abort](../../winscript/reference/idebugexpression-abort.md)    
 [IDebugExpression Arabirimi](../../winscript/reference/idebugexpression-interface.md)