---
title: 'Idebugcookie:: SetDebugCookie | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664939d0b91b8dbbf87dbff2978064811ffee486
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573177"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Hata ayıklama uygulaması tanımlama bilgisini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwDebugAppCookie`  
 'ndaki Hata ayıklama uygulamasını tanımlayan bir tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir işleme eklemek için birden fazla hata ayıklayıcıya izin veren hata ayıklama uygulaması tanımlama bilgisini ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugCookie Arabirimi](../../winscript/reference/idebugcookie-interface.md)