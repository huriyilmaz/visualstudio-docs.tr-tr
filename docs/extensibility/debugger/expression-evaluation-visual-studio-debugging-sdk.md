---
title: İfade Değerlendirme (Visual Studio Ayıklama SDK'sı) | Microsoft Docs
description: Kesme modu sırasında IDE, program değişkenlerini içeren ifadeleri değerlendirir. Hata ayıklama altyapısının bir ifadeyi nasıl ayrıştırıyor ve değerlendiriyor olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3c362b03dd6da91630b324fd659f0977c15a96c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043589"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade değerlendirmesi (Visual Studio AYıKLAMA SDK'sı)
Kesme modu sırasında, IDE'nin birkaç program değişkeni içeren basit ifadeleri değerlendirmesi gerekir. Değerlendirmesini gerçekleştirmek için hata ayıklama altyapısının (DE) IDE pencerelerinden biri içine girilen bir ifadeyi ayrıştırması ve değerlendirmesi gerekir.

 İfadeler [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemiyle oluşturulur ve sonuçta elde edilen [IDebugExpression2 arabirimiyle](../../extensibility/debugger/reference/idebugexpression2.md) temsil edilen.

 **IDebugExpression2** arabirimi DE tarafından uygulanır ve IDE'de ifade değerlendirmesinin sonuçlarını görüntülemek için IDE'ye bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini geri almak için **EvalAsync** yöntemini çağrır. [IDebugProperty2::GetPropertyInfo,](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) bir ifadenin değerini **bir İzleme** penceresine veya **YerelLer** penceresine koymak için kullanılan bir yapı döndürür.

 Hata ayıklama paketi veya oturum hata ayıklama yöneticisi (SDM), değerlendirmenin sonucu temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi almak için [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync'i](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) arar. `IDebugProperty2` ifadenin adını, türünü ve değerini iade eden yöntemleri vardır. Bu bilgiler çeşitli hata ayıklayıcı pencerelerinde görünür.

## <a name="using-expression-evaluation"></a>İfade değerlendirmesini kullanma
 İfade değerlendirmesini kullanmak için aşağıdaki tabloda gösterildiği gibi [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini ve [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabiriminin tüm yöntemlerini uygulamalısınız.

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bir ifadeyi zaman uyumsuz olarak değerlendirir.|
|[Iptal](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz ifade değerlendirmesini sona erer.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bir ifadeyi zaman uyumlu olarak değerlendirir.|

 Zaman uyumlu ve zaman uyumsuz değerlendirme, [IDebugProperty2::GetPropertyInfo yönteminin uygulanmasını](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gerektirir. Zaman uyumsuz ifade değerlendirmesi [için IDebugExpressionEvaluationCompleteEvent2 uygulaması gerekir.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
