---
title: 'IDebugApplicationNode:: EnumChildren | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.EnumChildren
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906f437d94d3ed8f50204930eddb1891b80b7cc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574799"
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
Bu uygulama düğümünün alt düğümlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pperddp`  
 dışı Bu düğümün alt düğümlerinin numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulama düğümünün alt düğümlerini numaralandırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)