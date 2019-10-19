---
title: 'Idebugexpression:: GetResultAsDebugProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575922"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Bir hata ayıklama özelliği ve işlemin dönüş değeri olarak ifade değerlendirmesinin sonucunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phrResult`  
 dışı İşlemin dönüş değeri.  
  
 `ppdp`  
 dışı İfadenin hata ayıklama özelliği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_PENDING`|İşlem hala beklemede.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `IDebugProperty` olarak ifade değerlendirmesinin sonucunu ve işlem `HRESULT` döndürür.  
  
 Bu yöntem `S_OK` döndürür ve `Abort` işlemi iptal ettiğinde `E_ABORT` `phrResult` döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugexpression arabirimi](../../winscript/reference/idebugexpression-interface.md)    
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)