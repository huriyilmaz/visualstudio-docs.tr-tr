---
title: Idebugapplicationthreadevents110 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984402"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 Arabirimi
Daha fazla iş parçacığı olayı ekler. Bu olaylar yalnızca yereldir. Diğer bir deyişle, PDM uygulama iş parçacığı nesnelerinde ( [ıdebugapplicationthread arabirimini](../../winscript/reference/idebugapplicationthread-interface.md)uygulayan nesneler) [ınewctionpoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) Advise ve Unadvise yöntemlerini kullanarak bunlara yalnızca hata ayıklanan işlemde abone olabilirsiniz. Bunlar, geldiği iş parçacığında meydana gelir.  
  
> [!IMPORTANT]
> Bu arabirim PDM v11.0 ve sonraki sürümler tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 `IDebugActivationThreadEvents110` arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|PDM 'in iş parçacığı geçişini kullanarak iş parçacığına çağrı başladı.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|İş parçacığı bir kesme noktasından devam ediyor ve bir kez daha etkin olacak.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|İş parçacığı bir kesme noktası için askıya alındı ve iş parçacığının tamamen askıya alınmasını gerektiren çağrıları işleyebilir.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|PDM öğesinin iş parçacığı geçişini kullanarak iş parçacığına çağrı tamamlandı.|