---
description: Bir iş parçacığını askıya alır.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f80799961ccce4b3492b46801b1917055742666
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164454"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Bir iş parçacığını askıya alır.

## <a name="syntax"></a>Sözdizimi

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
