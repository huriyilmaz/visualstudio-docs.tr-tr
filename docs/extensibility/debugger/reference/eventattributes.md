---
title: OLAY ÖZELLIKLERI | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737065"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Olay özniteliklerini belirtir.

## <a name="syntax"></a>Sözdizimi

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
Olayın eşzamanlı olduğunu ve olaya yanıt gerekmediğini gösterir.

`EVENT_SYNCHRONOUS`\
Olayın eşzamanlı olduğunu gösterir; [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)ile cevap verin.

`EVENT_STOPPING`\
Bunun bir durdurma olayı olduğunu gösterir. Ya da `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`.

`EVENT_ASYNC_STOP`\
Bir eşzamanlı durdurma olayını gösterir. Şu anda böyle bir olay yok. Bu bayrak sadece bir yer tutucu.

`EVENT_SYNC_STOP`\
Senkron durdurma olayını (bir arada `EVENT_SYNCHRONOUS` `EVENT_STOPPING`ve) gösterir. Bu değer, bir durdurma olayı gönderdiğinde hata ayıklama altyapısı (DE) tarafından kullanılır. Yanıt, [Yürütme,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) [Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)veya [Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md)çağrısı yoluyla yapılır.

`EVENT_IMMEDIATE`\
Hemen ve eşzamanlı olarak IDE'ye gönderilen bir olayı gösterir. Bu `EVENT_ASYNCHRONOUS`bayrak, `EVENT_SYNCHRONOUS`olayın türünü ve `EVENT_SYNC_STOP` yanıt mekanizmasının (varsa) bilindiğini belirtmek için diğer bayraklarla birleştirilir.

`EVENT_EXPRESSION_EVALUATION`\
Olay ifade değerlendirme nin bir sonucudur.

## <a name="remarks"></a>Açıklamalar
Bu değerler [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) `dwAttrib` yönteminin parametresinde geçirilir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
