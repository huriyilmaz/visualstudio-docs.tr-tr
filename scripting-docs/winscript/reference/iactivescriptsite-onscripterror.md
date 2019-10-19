---
title: 'IActiveScriptSite:: OnScriptError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570276"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Altyapı betiği çalıştırırken bir yürütme hatası oluştuğunu konağa bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pase`  
 'ndaki Hata nesnesinin [ıactivescripterror](../../winscript/reference/iactivescripterror.md) arabiriminin adresi. Bir konak, yürütme hatası hakkında bilgi edinmek için bu arabirimi kullanabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hata doğru şekilde işlenirse `S_OK`, aksi takdirde bir OLE tanımlı hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)