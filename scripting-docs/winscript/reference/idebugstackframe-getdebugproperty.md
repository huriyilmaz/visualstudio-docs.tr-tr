---
title: 'Idebugstackframe:: GetDebugProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 452c08bb0319167c0dfc1de86bf38a993e3cbad8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574275"
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
Geçerli çerçeve için bir özellik tarayıcısı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppDebugProp`  
 dışı Geçerli çerçeve için bir özellik tarayıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem geçerli çerçeve için bir özellik tarayıcısı döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugStackFrame Arabirimi](../../winscript/reference/idebugstackframe-interface.md)