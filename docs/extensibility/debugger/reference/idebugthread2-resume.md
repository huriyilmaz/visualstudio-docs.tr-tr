---
title: IDebugThread2::Devam | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718680"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Bir iş parçacığının yürütülmesini devam ettirer.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametreler
`pdwSuspendCount`\
[çıkış] Devam işleminden sonra askıya alma sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yönteme yapılan her çağrı, askıya alma sayısını 0'a ulaşına kadar erteler ve bu sırada yürütme ye devam edilir. Bu askıya alma **sayısı, İş Parçacıkları** hata ayıklama penceresinde görüntülenir.

 Bu yönteme yapılan her çağrı için Askıya [Alma](../../../extensibility/debugger/reference/idebugthread2-suspend.md) yöntemine daha önce bir çağrı olması gerekir. Askıya alma sayısı, yöntemin `IDebugThread2::Suspend` şimdiye kadar kaç kez çağrıldığını belirler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
