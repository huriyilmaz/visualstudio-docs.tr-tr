---
description: Adımlama için adım türünü belirtir.
title: STEPKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a972617b071f3c6f45a289a5fc01647bf3adee7fd9ebfa4ba4e2712c4774816
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276184"
---
# <a name="stepkind"></a>STEPKIND
Adımlama için adım türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Alanlar
 `STEP_INTO`\
 Bir işlevin adımları.

 `STEP_OVER`\
 Bir işlev üzerindeki adımlar.

 `STEP_OUT`\
 Bir işlevin adımları.

 `STEP_BACKWARDS`\
 Bir işleve geri doğru adımlar.

## <a name="remarks"></a>Açıklamalar
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
