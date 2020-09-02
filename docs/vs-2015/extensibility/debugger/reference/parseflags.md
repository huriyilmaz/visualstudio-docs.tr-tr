---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a9ebe244f3e1c1f3f95508d6df979edee2d4aed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205117"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir ifadenin nasıl ayrıştıralınacağını belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
## <a name="members"></a>Üyeler  
 PARSE_EXPRESSION  
 İfadenin bir deyim olmadığını gösterir.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 İfadenin adres olarak ayrıştırılacağını (ve daha sonra değerlendirildiğini) belirtir.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 İfadenin tasarım zamanı (bir tasarımcı açık olduğunda) sırasında ayrıştırılmakta olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ve [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) yöntemlerine parametre olarak geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
