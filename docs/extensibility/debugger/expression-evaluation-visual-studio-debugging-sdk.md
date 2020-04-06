---
title: İfade Değerlendirme (Visual Studio Hata Ayıklama SDK) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738716"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade değerlendirmesi (Visual Studio Hata Ayıklama SDK)
Kesme modu sırasında, IDE birkaç program değişkeni içeren basit ifadeleri değerlendirmek gerekir. Değerlendirmesini gerçekleştirmek için hata ayıklama altyapısının (DE) IDE pencerelerinden birine girilen bir ifadeyi ayrıştırması ve değerlendirmesi gerekir.

 İfadeler [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi ile oluşturulur ve ortaya çıkan [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi ile temsil edilir.

 **IDebugExpression2** arabirimi DE tarafından uygulanır ve IDE ifade değerlendirme sonuçlarını görüntülemek için [IDEbugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini IDE'ye döndürmek için **EvalAsync** yöntemini çağırır. [IDebugProperty2::GetPropertyInfo,](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) bir ifadenin değerini **Bir İzleme** penceresine veya Yerel **Ler** penceresine koymak için kullanılan bir yapıyı döndürür.

 Hata ayıklama paketi veya oturum hata ayıklama yöneticisi (SDM) [IDebugExpression2 çağırır::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) değerlendirme sonucunu temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi almak için. `IDebugProperty2`ifadenin adını, türünü ve değerini döndüren yöntemleri vardır. Bu bilgiler çeşitli hata ayıklama pencerelerinde görünür.

## <a name="using-expression-evaluation"></a>İfade değerlendirmesini kullanma
 İfade değerlendirmesini kullanmak için, aşağıdaki tabloda gösterildiği gibi [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini ve [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabiriminin tüm yöntemlerini uygulamanız gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bir ifadeyi eşzamanlı olarak değerlendirir.|
|[Durdurma](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Eşzamanlı ifade değerlendirmesini bitirir.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bir ifadeyi eşzamanlı olarak değerlendirir.|

 Senkron ve eşzamanlı değerlendirme [iDebugProperty2 uygulanmasını gerektirir::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi. Asynchronous ifade değerlendirmesi [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)uygulanmasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme kontrolü ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
