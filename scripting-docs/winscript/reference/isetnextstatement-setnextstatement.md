---
title: 'Isetnextdeyimin:: Setnextdeyimizi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.SetNextStatement
apilocation:
- scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8b940e603deb0aa9715e89b49eb1afdd28832ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571913"
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
Bu yöntem, komut dosyası yorumlayıcısının yürütebilmesi için bir sonraki kod bağlamını günceller.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStackFrame`  
 'ndaki Yığın çerçevesi nesnesine yönelik işaretçi.  
  
 `pCodeContext`  
 'ndaki Kod bağlamı nesnesine yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ISetNextStatement Arabirimi](../../winscript/reference/isetnextstatement-interface.md)