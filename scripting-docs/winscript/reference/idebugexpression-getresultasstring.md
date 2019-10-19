---
title: 'Idebugexpression:: Getresultasstrıng | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573522"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
İfade değerlendirmesinin sonucunu bir dize ve işlemin dönüş değeri olarak döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phrResult`  
 dışı İşlemin dönüş değeri.  
  
 `pbstrResult`  
 dışı İfade değerlendirmesinin sonucu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_PENDING`|İşlem hala beklemede.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ifade değerlendirmesinin sonucunu bir dize ve işlemin `HRESULT` döndürür.  
  
 Bu yöntem `S_OK` döndürür ve `Abort` işlemi iptal ettiğinde `E_ABORT` `phrResult` döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugExpression Arabirimi](../../winscript/reference/idebugexpression-interface.md)