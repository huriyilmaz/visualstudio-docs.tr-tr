---
title: PARSEFLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714114"
---
# <a name="parseflags"></a>PARSEFLAGS
Bir ifadenin nasıl ayrışdırılmasını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Alanlar
 `PARSE_EXPRESSION`\
 İfadenin bir deyim olmadığını gösterir.

 `PARSE_FUNCTION_AS_ADDRESS`\
 İfadenin adres olarak ayrıştırılması (ve daha sonra değerlendirileceğini) gösterir.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 İfadenin tasarım süresi boyunca ayrıştırıldığını gösterir (diğer bir tasarımcı açıkken).

## <a name="remarks"></a>Açıklamalar
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ve [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) yöntemlerine parametre olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
