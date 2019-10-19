---
title: 'IDebugApplicationNode:: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.GetParent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::GetParent
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c887e61652da8780012d98354f028f3e5cb005c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574767"
---
# <a name="idebugapplicationnodegetparent"></a>IDebugApplicationNode::GetParent
Bu uygulama düğümünün üst düğümünü döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pprddp`  
 dışı Bu uygulama düğümünün üst uygulama düğümü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulama düğümünün üst düğümünü döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)