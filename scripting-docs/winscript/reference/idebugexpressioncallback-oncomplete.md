---
title: 'Idebugexpressioncallback:: Ontamam| Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionCallBack.onComplete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExpressionCallBack::onComplete
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd142cc7ecbcd984be1943da05fa782260b10f8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576416"
---
# <a name="idebugexpressioncallbackoncomplete"></a>IDebugExpressionCallBack::onComplete
İfade değerlendirmesinin tamamlandığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ifade değerlendirmesi tamamlandığında çağrılır. `IDebugExpression::GetResultAsString` yöntemi bu olay işleyicisinin içinden çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugexpressioncallback arabirimi](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)