---
title: 'Iremotedebugapplicationevents:: OnEnterBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnEnterBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnEnterBreakPoint
ms.assetid: e92a56a3-c462-4a76-8ae8-4b2e6836a711
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad7b0dc3e4b6cd7e8779208121d7464e83e7bb3f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571991"
---
# <a name="iremotedebugapplicationeventsonenterbreakpoint"></a>IRemoteDebugApplicationEvents::OnEnterBreakPoint
Kesme noktası girmek için bir olay işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnEnterBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `prdat`  
 'ndaki Kesme noktasına girilen uygulama iş parçacığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, kesme noktası girmek için bir olayı işler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplicationEvents Arabirimi](../../winscript/reference/iremotedebugapplicationevents-interface.md)