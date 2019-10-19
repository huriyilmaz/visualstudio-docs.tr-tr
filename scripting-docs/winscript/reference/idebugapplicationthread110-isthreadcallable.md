---
title: 'Idebugapplicationthread110:: Isthreadçağrılabilir | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574474"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Bu iş parçacığının, PDM iş parçacığı geçiş mekanizmaları kullanılarak yapılan çağrıları işleyecek bir durumda olup olmadığını belirler, örneğin, SynchronousCallInThread.  
  
> [!IMPORTANT]
> [Idebugapplicationthread110 ARABIRIMI](../../winscript/reference/idebugapplicationthread110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pfIsCallable`  
 [out] iş parçacığı çağrılabilir `true`, aksi takdirde `false`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationThread110 Arabirimi](../../winscript/reference/idebugapplicationthread110-interface.md)