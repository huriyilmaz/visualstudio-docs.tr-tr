---
title: 'IRemoteDebugApplication:: ConnectDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed0ddeffd55475e1be4c9fab1e567d61a4b6654
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572327"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Bir hata ayıklayıcıyı bu uygulamaya bağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pad`  
 'ndaki Bu uygulamaya iliştirilecek hata ayıklayıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Bir hata ayıklayıcı zaten bu uygulamaya bağlı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir uygulama aynı anda yalnızca bir hata ayıklayıcı bağlı olabilir. Bir hata ayıklayıcı zaten bağlıysa, bu yöntem başarısız olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication:: GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)    
 [IRemoteDebugApplication Arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)