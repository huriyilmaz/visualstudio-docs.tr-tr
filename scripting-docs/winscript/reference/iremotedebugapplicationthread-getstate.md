---
title: 'Iremotedebugapplicationthread:: GetState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575246"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Bu iş parçacığının durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pState`  
 dışı Aşağıdaki iş parçacığı durum bayraklarının birleşimi:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|İş parçacığı çalışıyor.|  
|THREAD_STATE_SUSPENDED|0x00000002|İş parçacığı askıya alındı.|  
|THREAD_BLOCKED|0x00000004|İş parçacığı engellendi.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|İş parçacığı içeriği yetersiz.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu iş parçacığının durumunu alır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplicationThread Arabirimi](../../winscript/reference/iremotedebugapplicationthread-interface.md)