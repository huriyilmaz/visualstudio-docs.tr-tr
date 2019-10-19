---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575774"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Şu anda yürütülmekte olan iş parçacığı için bir komut dosyası motoru tanımlı tanımlayıcı alır. Tanımlayıcı, [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi gibi betik iş parçacığı yürütme denetimi yöntemlerine yapılan sonraki çağrılarda kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstidThread`  
 dışı Geçerli iş parçacığıyla ilişkili betik iş parçacığı tanımlayıcısını alan bir değişkenin adresi. Bu tanımlayıcının yorumu, komut dosyası motoruna bırakılır, ancak yalnızca Windows iş parçacığı tanımlayıcısının bir kopyası olabilir. Win32 iş parçacığı sonlandığında, bu tanımlayıcı atanmamış olur ve daha sonra başka bir iş parçacığına atanabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür ya da geçersiz bir işaretçi belirtilmişse `E_POINTER`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) arabirimine yol açmadan çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)