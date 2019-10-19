---
title: 'IActiveScriptSite:: OnStateChange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba8441d36f193f287dfec7406d5f136280c5a42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570156"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Ana bilgisayara, komut dosyası altyapısının durum değiştirmediğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ssScriptState`  
 'ndaki Yeni komut dosyası durumunu gösteren değer. Durumların açıklaması için [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) yöntemine bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)