---
title: 'IRemoteDebugApplication:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetName
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5689eb9153be0e9b6442ba505d618966f1421d39
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571995"
---
# <a name="iremotedebugapplicationgetname"></a>IRemoteDebugApplication::GetName
Bu uygulama düğümünün adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrName`  
 dışı Bu uygulama düğümünün adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulama düğümünün adını döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication Arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)