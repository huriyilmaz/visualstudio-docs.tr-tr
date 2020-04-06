---
title: IDebugExpression2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729694"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Bu arabirim, bağlama ve değerlendirmeiçin hazır ayrışmış bir ifadeyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bu arabirimi, değerlendirilmeye hazır ayrıştırılmış bir ifadeyi temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) için bir çağrı bu arabirimi döndürür. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini döndürür. Bu arabirimlere yalnızca debugged olan program duraklatılmış ve bir yığın çerçeve kullanılabilir olduğunda erişilebilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugExpression2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bu ifadeyi eşzamanlı olarak değerlendirir.|
|[Durdurma](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Eşzamanlı ifade değerlendirmesini bitirir.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bu ifadeyi eşzamanlı olarak değerlendirir.|

## <a name="remarks"></a>Açıklamalar
 Bir program durdurulduğunda, oturum hata ayıklama yöneticisi (SDM) [EnumFrameInfo'ya](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)bir çağrı yla DE'den bir yığın çerçevesi alır. SDM daha sonra [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini almak için [GetExpressionContext'ı](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) arar. Bunu, değerlendirilmeye hazır ayrıştırılmış ifadeyi temsil eden `IDebugExpression2` arabirimi oluşturmak için [ParseText'e](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yapılan çağrı takip eder.

 SDM, ifadeyi gerçekten değerlendirmek ve bir değer üretmek için [Sync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync'i](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) çağırır.

 Bir `IDebugExpressionContext2::ParseText`uygulamada, DE com `CoCreateInstance` işlevini bir ifade değerlendiricisi anlık ve bir [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi almak `IDebugExpressionEvaluator` için kullanır (arabirimdeki Örnek bakınız). DE daha sonra Bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi elde etmek için [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır. Bu arabirim in uygulanmasında `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` ve değerlendirmenin gerçekleminde kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
