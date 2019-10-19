---
title: 'Iapplicationdebugger:: onHandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577838"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Kesme noktası olayını işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `prpt`  
 'ndaki Kesme noktasının gerçekleştiği iş parçacığı.  
  
 `br`  
 'ndaki Kesme noktasının nedeni.  
  
 `pError`  
 'ndaki @No__t_0 değeri BREAKREASON_ERROR olduğunda, çalışma zamanı hata bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir kesme noktası isabet edildiğinde ve `IDebugApplication::HandleBreakPoint` çağrıldığında çağrılır.  
  
 Hata ayıklayıcı IDE `IRemoteDebugApplication::ResumeFromBreakPoint` çağırana kadar uygulama askıya alınır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iapplicationdebugger arabirimi](../../winscript/reference/iapplicationdebugger-interface.md)    
 [IDebugApplication:: HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)    
 [IRemoteDebugApplication:: ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)    
 [BREAKREASON Sabit Listesi](../../winscript/reference/breakreason-enumeration.md)