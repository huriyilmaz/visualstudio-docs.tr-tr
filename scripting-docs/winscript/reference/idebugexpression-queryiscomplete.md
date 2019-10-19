---
title: 'Idebugexpression:: Queryıstamam| Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c260ac5c02052f11f70e479588d65b71b4971267
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571968"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
İşlemin tamamlanıp tamamlanamayacağını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu ve işlem tamamlandı.|  
|`S_FALSE`|İşlem hala beklemede.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem işlemin tamamlanıp tamamlanamayacağını belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugExpression Arabirimi](../../winscript/reference/idebugexpression-interface.md)