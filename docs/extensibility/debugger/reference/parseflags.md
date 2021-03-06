---
description: Bir ifadenin nasıl ayrıştıralınacağını belirtir.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192e4de399540ce189bbf52cbb0f615b2b9bc855
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222152"
---
# <a name="parseflags"></a>PARSEFLAGS
Bir ifadenin nasıl ayrıştıralınacağını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Alanlar
 `PARSE_EXPRESSION`\
 İfadenin bir deyim olmadığını gösterir.

 `PARSE_FUNCTION_AS_ADDRESS`\
 İfadenin adres olarak ayrıştırılacağını (ve daha sonra değerlendirildiğini) belirtir.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 İfadenin tasarım zamanı (bir tasarımcı açık olduğunda) sırasında ayrıştırılmakta olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ve [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) yöntemlerine parametre olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
