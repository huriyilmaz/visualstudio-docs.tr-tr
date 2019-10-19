---
title: 'Idebugbelgethelper:: Getscriptblockınfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a92aa00d7997ceccc583c88a070f6fbc7d4359d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576095"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Bir betik bloğuna karşılık gelen karakter aralığını ve betik altyapısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwSourceContext`  
 'ndaki Betik bloğunun kaynak bağlamı.  
  
 `ppasd`  
 dışı Bu betik bloğunun betik altyapısı.  
  
 `piCharPos`  
 dışı Betik bloğunun başlangıç konumu.  
  
 `cChars`  
 dışı Betik bloğundaki karakter sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir betik bloğuna karşılık gelen karakter aralığını ve betik altyapısını alır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentHelper Arabirimi](../../winscript/reference/idebugdocumenthelper-interface.md)