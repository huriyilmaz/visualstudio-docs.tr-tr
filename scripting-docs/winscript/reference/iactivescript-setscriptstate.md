---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577998"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Komut dosyası altyapısını verilen duruma getirir. Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) arabirimine yol açmadan çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ss`  
 'ndaki Komut dosyası altyapısını belirtilen duruma ayarlar. [Scriptstate sabit](../../winscript/reference/scriptstate-enumeration.md) listesi numaralandırmasında tanımlanan değerlerden biri olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_FAIL`|Betik altyapısı, başlatılmış duruma geri geçişi desteklemez. Konağın bu komut dosyası altyapısını atıp aynı etkiyi elde etmek için yeni bir betik altyapısı oluşturması, başlatması ve yüklemesi gerekir.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış) ve bu nedenle başarısız oldu.|  
|`OLESCRIPT_S_PENDING`|Yöntem başarıyla sıraya alındı, ancak durum henüz değiştirilmedi. Durum değiştiğinde, site [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemi aracılığıyla geri çağırılır.|  
|`S_FALSE`|Yöntem başarılı oldu, ancak betik zaten verilen durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Scripting Engine durumları hakkında daha fazla bilgi için [Windows komut dosyası altyapılarının](../../winscript/windows-script-engines.md) komut dosyası altyapısı durumları bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse::P arseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)