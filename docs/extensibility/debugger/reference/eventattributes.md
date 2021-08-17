---
description: Olay özniteliklerini belirtir.
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c496e30b5d20bfad7b06e44660045e2e2394ed1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073077"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Olay özniteliklerini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Alanlar
`EVENT_ASYNCHRONOUS`\
Olayın zaman uyumsuz olduğunu ve olaya yanıt gerekmediğini gösterir.

`EVENT_SYNCHRONOUS`\
Olayın zaman uyumlu olduğunu belirtir; [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)aracılığıyla yanıtlayın.

`EVENT_STOPPING`\
Bunun bir durdurma olayı olduğunu gösterir. Ya da ile birleştirilmelidir `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Zaman uyumsuz durdurma olayını gösterir. Şu anda böyle bir olay yok. Bu bayrak yalnızca bir yer tutucudur.

`EVENT_SYNC_STOP`\
Zaman uyumlu durdurma olayını belirtir ( `EVENT_SYNCHRONOUS` ve birleşimi `EVENT_STOPPING` ). Bu değer, bir durdurma olayı gönderdiğinde bir hata ayıklama altyapısı (DE) tarafından kullanılır. Yanıt, [yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)ve [devam etme](../../../extensibility/debugger/reference/idebugprogram2-continue.md)çağrısı yoluyla yapılır.

`EVENT_IMMEDIATE`\
IDE 'ye anında ve zaman uyumlu olarak gönderilen bir olayı gösterir. Bu bayrak `EVENT_ASYNCHRONOUS` , `EVENT_SYNCHRONOUS` `EVENT_SYNC_STOP` olay türünü ve yanıt mekanizmasının (varsa) bilindiğini belirtmek için, veya gibi diğer bayraklarla birleştirilir.

`EVENT_EXPRESSION_EVALUATION`\
Olay, ifade değerlendirmesinin bir sonucudur.

## <a name="remarks"></a>Açıklamalar
Bu değerler `dwAttrib` [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) yönteminin parametresine geçirilir.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
