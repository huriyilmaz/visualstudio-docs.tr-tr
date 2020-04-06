---
title: EVALFLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737115"
---
# <a name="evalflags"></a>EVALFLAGS
İfade değerlendirmesini denetleyen bayraklar belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Alanlar
`EVAL_RETURNVALUE`\
Varsa iade değerinin değerlendirilmesi gerektiğini belirtir.

`EVAL_NOSIDEEFFECTS`\
Yan etkilere izin verilmemesini belirtir.

`EVAL_ALLOWBPS`\
Kesme noktalarında durmayı belirtir.

`EVAL_ALLOWERRORREPORT`\
İzin verilmesi için ana bilgisayara hata bildirimi ni belirtir. Öncelikle Internet Explorer'da komut dosyasında ifade değerlendirmesi için kullanılır.

`EVAL_FUNCTION_AS_ADDRESS`\
İşlev çağırmak yerine işlevleri adres olarak değerlendirilmeye zorlar.

`EVAL_NOFUNCEVAL`\
Fonksiyonun değerlendirilmesini engeller. Örneğin, ifadedeki `int` `myExpression(int) + 10`belirteci göz önünde bulundurun. Bu işlev doğru bir adres olarak değerlendirilebilir, ancak bir değer olarak değil.

`EVAL_NOEVENTS`\
İfade değerlendirmesi sırasında meydana gelen olayların oturum hata ayıklama yöneticisine (SDM) veya IDE'ye gönderilmemesi gerektiğini belirtmek için işaretle.

## <a name="remarks"></a>Açıklamalar
Bu [bayraklar, EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ve [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) yöntemlerine bağımsız değişken olarak geçirilir.

Bu bayraklar biraz veya biraz veya birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
