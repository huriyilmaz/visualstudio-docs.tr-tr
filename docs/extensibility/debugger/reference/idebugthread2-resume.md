---
title: 'IDebugThread2:: özgeçmişi | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718680"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Bir iş parçacığının yürütülmesini sürdürür.

## <a name="syntax"></a>Söz dizimi

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
dışı Yeniden başlatma işleminden sonra askıda kalma sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yönteme yapılan her bir çağrı, bu süre sonunda 0 olana kadar askıya alma sayısını azaltır, yürütme gerçekten sürdürülür. Bu askıya alma sayısı, **Iş parçacıkları** hata ayıklama penceresinde görüntülenir.

 Bu yönteme yapılan her çağrı için, [askıya alma](../../../extensibility/debugger/reference/idebugthread2-suspend.md) yöntemine önceki bir çağrı olmalıdır. Askıya alma sayısı, yöntemin şimdiye kadar kaç kez `IDebugThread2::Suspend` çağrıldığını belirler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
