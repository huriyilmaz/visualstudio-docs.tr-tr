---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 073dac8de37edddc1b748c52258047cd2d85e218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937081"
---
# <a name="evalflags"></a>EVALFLAGS
İfade değerlendirmesini denetleyen bayrakları belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS {
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
public enum enum_EVALFLAGS {
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
Varsa, dönüş değerinin değerlendirildiğini belirtir.

`EVAL_NOSIDEEFFECTS`\
Yan etkilere izin verilmeyeceğini belirtir.

`EVAL_ALLOWBPS`\
Kesme noktalarında durdurmayı belirtir.

`EVAL_ALLOWERRORREPORT`\
Konağa izin verilecek hata bildirimini belirtir. Birincil olarak Internet Explorer 'da betikte ifade değerlendirmesi için kullanılır.

`EVAL_FUNCTION_AS_ADDRESS`\
İşlevi çağırmak yerine işlevleri adres olarak değerlendirilmeye zorlar.

`EVAL_NOFUNCEVAL`\
İşlevin değerlendirilmesini engeller. Örneğin, `int` ifadedeki belirteci düşünün `myExpression(int) + 10` . Bu işlev, bir adres olarak doğru şekilde değerlendirilebil, ancak değer olarak değerlendirilemiyor.

`EVAL_NOEVENTS`\
İfade değerlendirmesi sırasında oluşan olayların, oturum hata ayıklama Yöneticisi 'ne (SDM) veya IDE 'ye gönderilmemesi gerektiğini belirten bayrak.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ve [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) yöntemlerine bir bağımsız değişken olarak geçirilir.

Bu bayraklar bit düzeyinde OR ile birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
