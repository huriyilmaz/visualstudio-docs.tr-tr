---
title: 'Imachinedebugmanagercookie:: Addadpplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da436308c71a66d3070d42128d8da03ae88d2935
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573909"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Çalışan uygulama listesine bir uygulama ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 'ndaki Uygulama, çalışan uygulama listesine.  
  
 `dwDebugAppCookie`  
 'ndaki Hata ayıklama uygulamasını tanımlayan bir tanımlama bilgisi.  
  
 `pdwAppCookie`  
 dışı Machine Debug Manager 'dan uygulamayı kaldırmak için kullanılan tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `IProcessDebugManager::AddApplication` her çağrıldığında işlem hata ayıklama Yöneticisi tarafından çağırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Imachinedebugmanagercookie arabirimi](../../winscript/reference/imachinedebugmanagercookie-interface.md)    
 [Imachinedebugmanagercookie:: RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)