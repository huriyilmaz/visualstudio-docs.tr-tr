---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570324"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Betik altyapısının yürütülen komut dosyası kodundan döndürdüğü konağa bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı, komut dosyası motoruna girilen bir çağıran uygulamaya denetim döndürmeden önce bu yöntemi çağırmalıdır. Örneğin, komut dosyası, daha sonra betik altyapısı tarafından işlenen bir olayı harekete geçirdikten sonra betik altyapısı, olayı yürütmeden önce [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metodunu çağırmalıdır ve olayı yürüttükten sonra `IActiveScriptSite::OnLeaveScript` çağırmalıdır olayı tetikleyen nesneye döndürmeden önce. Bu yönteme yapılan çağrılar iç içe olabilir. @No__t_0 yapılan her çağrıya, bu yönteme karşılık gelen bir çağrı gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)