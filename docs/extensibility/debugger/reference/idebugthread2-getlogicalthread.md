---
title: IDebugThread2::GetLogicalThread | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718844"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Hata ayıklama motorları bu yöntemi uygulamaz.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parametreler
`pStackFrame`\
[içinde] Yığın çerçevesini temsil eden bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`ppLogicalThread`\
[çıkış] İlişkili `IDebugLogicalThread2` mantıksal iş parçacığı temsil eden bir arabirim döndürür. Hata ayıklama altyapısı uygulaması bunu null bir değere ayarlamalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Hata ayıklama motoru `E_NOTIMPL`uygulamaları her zaman geri döner.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
