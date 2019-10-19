---
title: 'Idebugapplication110:: SynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573647"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Ana iş parçacığında zaman uyumlu bir çağrı yapar.  
  
> [!IMPORTANT]
> [Idebugapplication110 ARABIRIMI](../../winscript/reference/idebugapplication110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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