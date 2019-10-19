---
title: 'Idebugapplicationthread110:: IsSuspendedForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574453"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
[Idebugapplicationthreadevents110:: OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 'in bu iş parçacığında çağrılıp çağrılmadığını ve henüz tamamlanmadığını belirler.  
  
> [!IMPORTANT]
> [Idebugapplicationthread110 ARABIRIMI](../../winscript/reference/idebugapplicationthread110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pfIsSuspended`  
 [out] iş parçacığı bir kesme noktası için askıya alınırsa `true`, aksi takdirde `false`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationThread110 Arabirimi](../../winscript/reference/idebugapplicationthread110-interface.md)