---
title: 'Idebugformatter:: GetVariantForString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc230caa861444b10b463e5786d5f8cb93ec32f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571522"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Verilen dizeyi içeren bir DEĞIŞKEN döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwstrValue`  
 'ndaki Bir DEĞIŞKEN içinde depolanacak dize.  
  
 `pvar`  
 dışı @No__t_0 içeren DEĞIŞKEN.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, verilen dizeyi içeren bir DEĞIŞKEN döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugFormatter Arabirimi](../../winscript/reference/idebugformatter-interface.md)