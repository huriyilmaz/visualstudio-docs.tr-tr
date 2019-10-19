---
title: 'Ihata ayıklama Gasyncoperation:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573306"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Bir işlemi iptal eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|S_OK|Yöntem başarılı oldu.|  
|E_NOTIMPL|İşlemler iptal edilemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem genellikle, yanıt vermeyen bir işlemi iptal etmek için hata ayıklayıcı iş parçacığı içinden çağırılır. Bu yöntem, `IDebugSyncOperation` nesnesindeki `InProgressAbort` yönteminin çağrılmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Gasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)    
 [Ihata ayıklama Gasyncoperation:: Start](../../winscript/reference/idebugasyncoperation-start.md)    
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)