---
title: 'Idebugsessionproviderex: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfe26265d56b2179feeac2a9802940258074b1c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574304"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Belirtilen uygulamayla bir hata ayıklama oturumu başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 'ndaki Hata ayıklama uygulamasını belirtir.  
  
 `fQuery`  
 'ndaki True, bir sorguyu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen uygulamayla bir hata ayıklama oturumu başlatır. Hata ayıklayıcı, bu çağrıdan döndürmeden önce `IRemoteDebugApplication::ConnectDebugger` çağırmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugsessionproviderex arabirimi](../../winscript/reference/idebugsessionproviderex-interface.md)    
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)