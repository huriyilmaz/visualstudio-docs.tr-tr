---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578002"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Bir betik iş parçacığının geçerli durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stidThread`  
 'ndaki Durumun istendiği iş parçacığının tanımlayıcısı veya aşağıdaki özel iş parçacığı tanımlayıcılarından biri:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısının örneklendiği iş parçacığı.|  
|SCRIPTTHREADID_CURRENT|Yürütülmekte olan iş parçacığı.|  
  
 `pstsState`  
 dışı Belirtilen iş parçacığının durumunu alan bir değişkenin adresi. Durum, [Scriptthreadstate numaralandırma](../../winscript/reference/scriptthreadstate-enumeration.md) numaralandırması tarafından tanımlanan adlandırılmış sabit değerlerden biriyle gösterilir. Bu parametre geçerli iş parçacığını tanımlamaz, durum herhangi bir zamanda değişebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) arabirimine yol açmadan çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)