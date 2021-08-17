---
description: İfade değerlendirmesini denetleyen bayrakları belirtir.
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00b025ac3d14ee9c2d6bd767ff45c28222c71009ffe6702e183ffe705e3eaf31
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390300"
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
