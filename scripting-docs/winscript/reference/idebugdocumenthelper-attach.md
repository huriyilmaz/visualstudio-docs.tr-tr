---
title: 'Idebugbelgethelper:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577027"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Belge ağacına bu belgeyi ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pddhParent`  
 'ndaki Bu belgenin ekleneceği belge ağacı. NULL olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu belgeyi üst öğe olarak `pddhParent` kullanarak belge ağacına ekler. `pddhParent` `NULL`, bu belge üst düzey belge olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper::D etach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper Arabirimi](../../winscript/reference/idebugdocumenthelper-interface.md)