---
title: 'IDebugApplication:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575005"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Hata ayıklayıcının `IApplicationDebugger` arabirimine genel bir olay harekete geçirilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki Nesne için bir GUID.  
  
 `punk`  
 'ndaki Hata ayıklayıcıya geçirilecek bir olay nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Yöntem şu anda uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 GUID ve `IUnknown` semantiği, tamamen uygulama/hata ayıklayıcı tanımlı bir uygulamadır.  
  
 Bu yöntem, hata ayıklayıcı modelinin özel uzantılarına izin verir; Şu anda uygulanmadı.  
  
 Bu yöntem `IApplicationDebugger::onDebuggerEvent` çağırmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)    
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)