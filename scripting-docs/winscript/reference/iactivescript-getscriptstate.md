---
title: 'IActiveScript:: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575733"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Komut dosyası altyapısının geçerli durumunu alır. Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) arabirimine yol açmadan çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pss`  
 dışı [Scriptstate sabit](../../winscript/reference/scriptstate-enumeration.md) listesi numaralandırmasında tanımlanan bir değeri alan bir değişkenin adresi. Değer, çağıran iş parçacığıyla ilişkili komut dosyası altyapısının geçerli durumunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür ya da geçersiz bir işaretçi belirtilmişse `E_POINTER`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)