---
title: 'IActiveScript:: Getscriptthreadıd | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575699"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Verilen Win32 iş parçacığıyla ilişkili iş parçacığı için bir komut dosyası motoru tanımlı tanımlayıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwWin32ThreadID`,  
 'ndaki Geçerli işlemde çalışan bir Win32 iş parçacığının iş parçacığı tanımlayıcısı. Şu anda yürütülmekte olan iş parçacığının iş parçacığı tanımlayıcısını almak için [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) işlevini kullanın.  
  
 `pstidThread`,  
 dışı Verilen Win32 iş parçacığı ile ilişkili betik iş parçacığı tanımlayıcısını alan bir değişkenin adresi. Bu tanımlayıcının yorumu, komut dosyası motoruna bırakılır, ancak yalnızca Windows iş parçacığı tanımlayıcısının bir kopyası olabilir. Win32 iş parçacığı sonlandırıldığında, bu tanımlayıcı atanmamış olur ve daha sonra başka bir iş parçacığına atanabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış) ve bu nedenle başarısız oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alınan tanımlayıcı, [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi gibi betik iş parçacığı yürütme denetimi yöntemlerine sonraki çağrılarında kullanılabilir.  
  
 Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) arabirimine neden olmadan çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)