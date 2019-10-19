---
title: 'Idebugapplicationnodeevents:: onAddChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052fe47f1ddf2d20e7486a95a9dd79bc388f7ebc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574703"
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Bir alt düğüm bir hata ayıklama uygulama düğümü nesnesine eklendiğinde olayı işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `prddpChild`  
 'ndaki Eklenen alt hata ayıklama uygulama düğümü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir alt düğüm bir hata ayıklama uygulama düğümü nesnesine eklendiğinde olayı işler.  
  
 @No__t_0 arabiriminin uygulayıcıları bu olayı yükseltir  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugapplicationnodeevents arabirimi](../../winscript/reference/idebugapplicationnodeevents-interface.md)    
 [Idebugapplicationnodeevents:: onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)    
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)