---
title: 'IDebugApplicationNode:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574779"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Bu uygulama düğümünü belirtilen proje ağacına ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdanParent`  
 'ndaki Bu uygulama düğümünün ekleneceği proje ağacı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulama düğümünü üst öğe olarak `pdanParent` kullanarak proje ağacına ekler. `pdanParent` `NULL`, bu uygulama düğümü en üst düzey düğüm olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationNode::D etach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)