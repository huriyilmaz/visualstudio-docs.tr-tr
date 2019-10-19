---
title: 'Isetnextdeyimin:: Cansetnextdeyimizi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571846"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Bu yöntem, çalıştırılacak bir sonraki kod ifadesini belirleyen yürütme noktasının belirtilen konuma ayarlanamayacağını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CanSetNextStatement(  
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
|`S_OK`|Sonraki ifade belirtilen kod bağlamına güncelleştirilebilen olabilir.|  
|`S_FALSE`|Sonraki ifade belirtilen kod bağlamına güncelleştirilemez.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ISetNextStatement Arabirimi](../../winscript/reference/isetnextstatement-interface.md)