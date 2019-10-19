---
title: 'Imachinedebugmanagerevents:: Onaddadpplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onAddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onAddApplication
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe710ce9a126e344fc88024b7bf5fd2b993e31b3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576113"
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Çalışan uygulama listesine bir uygulama eklendiğinde olayı işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 'ndaki Çalışan uygulama listesine eklenen uygulama.  
  
 `dwAppCookie`  
 'ndaki Uygulama uygulama listesine eklendiğinde belirtilen tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, çalışan uygulama listesine bir uygulamanın eklendiğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Imachinedebugmanagerevents arabirimi](../../winscript/reference/imachinedebugmanagerevents-interface.md)    
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)