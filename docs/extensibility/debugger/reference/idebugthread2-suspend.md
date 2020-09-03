---
title: 'IDebugThread2:: Suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718644"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Bir iş parçacığını askıya alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametreler
`pdwSuspendCount`\
dışı Askıya alma işleminden sonra askıda kalma sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yönteme yapılan her çağrı 0 ' dan sonraki askıya alma sayısını artırır. Bu askıya alma sayısı, **Iş parçacıkları** hata ayıklama penceresinde görüntülenir.

 Bu yönteme yapılan her çağrı için, daha sonra [sürdürülmesi](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemine bir çağrı olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
