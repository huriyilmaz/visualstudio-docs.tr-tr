---
title: 'Idebugapplication110:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575080"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Bu iş parçacığına iş parçacıkları arası çağrıların nakledilmesine izin verirken belirtilen tanıtıcılardan herhangi birinin sinyal gönderilmesini bekler. Bu yöntemin hata ayıklayıcı iş parçacığından çağrılması gerekir.  
  
> [!IMPORTANT]
> [Idebugapplication110 ARABIRIMI](../../winscript/reference/idebugapplication110-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `handleCount`  
 Beklenecek tanıtıcı sayısı.  
  
 `pHandles`  
 Bekleyecek tutamaçlar kümesi.  
  
 `pIndex`  
 HRESULT değeri S_OK olduğunda, işaret edilen tanıtıcı için `pHandles` dizin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication110 Arabirimi](../../winscript/reference/idebugapplication110-interface.md)