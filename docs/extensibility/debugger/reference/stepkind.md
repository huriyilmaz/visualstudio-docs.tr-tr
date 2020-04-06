---
title: STEPKIND | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ed2877c880d3cd2674f62b4f900a6e923bb29d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713552"
---
# <a name="stepkind"></a>STEPKIND
Adım atmak için adım türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Alanlar
 `STEP_INTO`\
 Bir işleve adım atar.

 `STEP_OVER`\
 Bir işlevin üzerine basarsa.

 `STEP_OUT`\
 Bir işlevin dışına adım.

 `STEP_BACKWARDS`\
 Bir işleve geriye doğru adım atar.

## <a name="remarks"></a>Açıklamalar
 [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md) yöntemine bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
