---
description: Bir ifadenin nasıl ayrıştırılası olduğunu belirtir.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd615c80c23ce3714208b7b09d1de8480698f52c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034701"
---
# <a name="parseflags"></a>PARSEFLAGS
Bir ifadenin nasıl ayrıştırılası olduğunu belirtir.

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
 İfadenin bir adres olarak ayrıştır (ve daha sonra değerlendirilecek) olduğunu gösterir.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 İfadenin tasarım zamanında (yani tasarımcı açık olduğunda) ayrıştırıldı olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 ParseText ve [Parse yöntemlerine](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) [parametre olarak](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
