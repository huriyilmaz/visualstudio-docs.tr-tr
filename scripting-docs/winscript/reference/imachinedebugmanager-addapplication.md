---
title: 'Imachinedebugmanager:: Addadpplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573963"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Çalışan uygulama listesine bir uygulama ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 'ndaki Uygulama, çalışan uygulama listesine.  
  
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
 [Imachinedebugmanager arabirimi](../../winscript/reference/imachinedebugmanager-interface.md)    
 [Imachinedebugmanager:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)