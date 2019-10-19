---
title: 'Ihata ayıklama Gasyncoperation:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573252"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Zaman uyumsuz işlemin başlamasını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `padocb`  
 Bu işlemden durum olaylarını alan geri çağırma arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_UNEXPECTED`|Bir işlem zaten bekliyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `IDebugSyncOperation::GetTargetThread` alınan iş parçacığında `IDebugSyncOperation::Execute` zaman uyumsuz olarak çağrılmasına neden olur. Bu yöntem yalnızca hata ayıklayıcı iş parçacığı içinden çağrılmalıdır; Aksi takdirde, işlem tamamlanana kadar dönemeyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Gasyncoperation:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)    
 [Ihata ayıklama Gasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)    
 [Idebugsyncoperation:: Execute](../../winscript/reference/idebugsyncoperation-execute.md)    
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)