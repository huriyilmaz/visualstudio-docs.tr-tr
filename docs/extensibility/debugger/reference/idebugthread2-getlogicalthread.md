---
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718844"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Hata ayıklama motorları bu yöntemi uygulamaz.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Yığın çerçevesini temsil eden bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`ppLogicalThread`\
dışı `IDebugLogicalThread2` İlişkili mantıksal iş parçacığını temsil eden bir arabirim döndürür. Bir hata ayıklama altyapısı uygulamasının bunu null bir değere ayarlaması gerekir.

## <a name="return-value"></a>Dönüş Değeri
 Hata ayıklama altyapısı uygulamaları her zaman döndürülür `E_NOTIMPL` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
