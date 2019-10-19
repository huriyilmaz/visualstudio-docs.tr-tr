---
title: 'Idebugapplicationthread110:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574484"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
PDM 'in Şu anda işlenmekte olan iş parçacığı geçiş mekanizmalarından iş parçacığı isteklerinin sayısını döndürür. Bu sayı genellikle 0 veya 1 ' dir. Ancak, bir iş parçacığı çağrısının işleme başlaması, ancak iş parçacığından zaman uyumlu bir çağrı tetiklenmesi veya iş parçacığını askıya almasına izin vermek için (örneğin, bir ıremotedebugapplicationevents tetiklenerek) numara daha yüksek olabilir. [ ](../../winscript/reference/iremotedebugapplicationevents-interface.md)Hata ayıklayıcı iş parçacığı üzerinde verilen arabirim olayı.  
  
> [!IMPORTANT]
> [Idebugapplicationthread110 ARABIRIMI](../../winscript/reference/idebugapplicationthread110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `puiThreadRequests`  
 dışı İş parçacığı isteklerinin sayısı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationThread110 Arabirimi](../../winscript/reference/idebugapplicationthread110-interface.md)