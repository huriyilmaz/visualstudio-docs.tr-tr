---
title: 'Idebugapplicationnodeevents:: onAttach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574687"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Hata ayıklama uygulama düğümü nesnesinin bir üst düğüme iliştirilmesiyle ilgili bir olayı işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `prddpParent`  
 'ndaki Bu düğümün üst öğesi olan hata ayıklama uygulaması düğümü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulama düğümü nesnesinin bir üst düğüme eklendiği belirten bir olayı işler.  
  
 @No__t_0 arabiriminin uygulayıcıları bu olayı yükseltir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugapplicationnodeevents arabirimi](../../winscript/reference/idebugapplicationnodeevents-interface.md)    
 [Idebugapplicationnodeevents:: onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)    
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)