---
title: STEPUNIT | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a87c86647407d90c9f4292b1307fd5623e85d13b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713517"
---
# <a name="stepunit"></a>STEPUNIT
Adım atmak için adım birimini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Alanlar
 `STEP_STATEMENT`\
 İfadeye göre adımlar.

 `STEP_LINE`\
 Adım adım.

 `STEP_INSTRUCTION`\
 Talimatla adımlar.

## <a name="remarks"></a>Açıklamalar
 [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md) yöntemine bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
