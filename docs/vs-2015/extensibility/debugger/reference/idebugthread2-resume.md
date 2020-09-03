---
title: 'IDebugThread2:: özgeçmişi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152985"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir iş parçacığının yürütülmesini sürdürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwSuspendCount`  
 dışı Yeniden başlatma işleminden sonra askıda kalma sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönteme yapılan her bir çağrı, bu süre sonunda 0 olana kadar askıya alma sayısını azaltır, yürütme gerçekten sürdürülür. Bu askıya alma sayısı, **Iş parçacıkları** hata ayıklama penceresinde görüntülenir.  
  
 Bu yönteme yapılan her çağrı için, [askıya alma](../../../extensibility/debugger/reference/idebugthread2-suspend.md) yöntemine önceki bir çağrı olmalıdır. Askıya alma sayısı, yöntemin şimdiye kadar kaç kez `IDebugThread2::Suspend` çağrıldığını belirler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
