---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570357"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Komut dosyası altyapısının betik kodunu yürütmeye başladığını ana bilgisayara bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı her girişte bu yöntemi çağırmalıdır veya betik motoruna yeniden giriş yapmanız gerekir. Örneğin, komut dosyası, daha sonra betik altyapısı tarafından işlenen bir olayı harekete geçirdikten sonra betik altyapısı, olayı yürütmeden önce `IActiveScriptSite::OnEnterScript` çağırmalıdır ve olayı yürüttükten sonra [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) metodunu çağırmalıdır Ancak olayı tetikleyen nesneye dönmeden önce. Bu yönteme yapılan çağrılar iç içe olabilir. Bu yönteme yapılan her çağrıda `IActiveScriptSite::OnLeaveScript` için karşılık gelen bir çağrı gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)