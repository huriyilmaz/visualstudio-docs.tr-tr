---
title: 'IDebugApplicationNode:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Close
ms.assetid: ea8db480-2344-4c7b-960c-4fa97fa6c1b7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 928dc94a5d700b2cad6a7acfb59a409240be7dc3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574837"
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Bu uygulamanın tüm başvuruları serbest bırakmaya ve etkin olmayan bir durum girmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, uygulama çıktığında uygulamanın sahibi bu yöntemi çağırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationNode Arabirimi](../../winscript/reference/idebugapplicationnode-interface.md)