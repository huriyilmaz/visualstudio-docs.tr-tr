---
description: İfade değerlendirmesini kontrol eden bayrakları belirtir.
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
ms.openlocfilehash: 18e6f019bb6a06d9c1718239b69c6a80dd4fd434
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080058"
---
# <a name="evalflags"></a>EVALFLAGS
İfade değerlendirmesini kontrol eden bayrakları belirtir.

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
Varsa dönüş değerinin değerlendirilecek olduğunu belirtir.

`EVAL_NOSIDEEFFECTS`\
Yan etkilere izin verilmiyor olduğunu belirtir.

`EVAL_ALLOWBPS`\
Kesme noktalarında durdurmayı belirtir.

`EVAL_ALLOWERRORREPORT`\
İzin verilen ana bilgisayar için hata raporlamayı belirtir. Öncelikle betikte ifade değerlendirmesi için kullanılır Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
İşlevleri adres olarak değerlendirilmeye, işlevin değerlendirilmesine neden olur.

`EVAL_NOFUNCEVAL`\
İşlevin değerlendirilmesini önler. Örneğin, ifadesinde `int` belirteci göz önünde `myExpression(int) + 10` bulundurarak. Bu işlev bir adres olarak doğru şekilde değerlendirebilirsiniz ancak değer olarak değerlendirilmez.

`EVAL_NOEVENTS`\
İfade değerlendirmesi sırasında meydana gelen olayların oturum hata ayıklama yöneticisine (SDM) veya IDE'ye gönderilmez olduğunu belirten bayrak.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar [EvaluateAsync ve EvaluateSync yöntemlerine bağımsız](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) değişken [olarak](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) geçirildi.

Bu bayraklar bitwise OR ile birleştirilmiş olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
