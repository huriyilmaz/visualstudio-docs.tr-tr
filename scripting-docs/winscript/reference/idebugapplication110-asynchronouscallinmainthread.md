---
title: 'Idebugapplication110:: AsynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577399"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Ana iş parçacığında zaman uyumsuz bir çağrı yapar.  
  
> [!IMPORTANT]
> [Idebugapplication110 ARABIRIMI](../../winscript/reference/idebugapplication110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pptc`  
 Çağrılacak [ıdebugthreadcall arabirim](../../winscript/reference/idebugthreadcall-interface.md) nesnesi.  
  
 `dwParam1`  
 Çağrının ilk parametresi.  
  
 `dwParam1`  
 Çağrının ilk parametresi.  
  
 `dwParam2`  
 Çağrının ikinci parametresi.  
  
 `dwParam3`  
 Çağrının üçüncü parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication110 Arabirimi](../../winscript/reference/idebugapplication110-interface.md)