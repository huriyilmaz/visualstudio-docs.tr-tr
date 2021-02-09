---
title: İfade değerlendirmesi (Visual Studio hata ayıklama SDK) | Microsoft Docs
description: Kesme modu sırasında, IDE program değişkenlerini içeren ifadeleri değerlendirir. Hata ayıklama altyapısının bir ifadeyi nasıl ayrıştırır ve değerlendirdiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 772d38b328eca1e0afb6ff48a5ad580d01939527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921472"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade değerlendirmesi (Visual Studio hata ayıklama SDK)
Kesme modu sırasında IDE, çeşitli program değişkenlerini kapsayan basit ifadeleri değerlendirmelidir. Kendi değerlendirmesini gerçekleştirmek için, hata ayıklama altyapısı (DE), IDE 'nin bir pencerelerinin birine girilen bir ifadeyi ayrıştırmalıdır ve değerlendirmelidir.

 İfadeler, [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemiyle oluşturulur ve elde edilen [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi tarafından temsil edilir.

 **IDebugExpression2** arabirimi de tarafından UYGULANıR ve IDE 'de ifade değerlendirmesinin sonuçlarını göstermek için **EVALASYNC** yöntemini çağırarak IDE 'ye bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , bir ifadenin değerini bir **Gözcü** penceresine veya **Locals** penceresine koymak için kullanılan bir yapı döndürür.

 Hata ayıklama paketi veya oturum hata ayıklama Yöneticisi (SDM), değerlendirmenin sonucunu temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi almak için [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır. `IDebugProperty2` ifadenin adını, türünü ve değerini döndüren yöntemlere sahiptir. Bu bilgiler çeşitli hata ayıklayıcı pencereleri içinde görüntülenir.

## <a name="using-expression-evaluation"></a>İfade değerlendirmesini kullanma
 İfade değerlendirmesini kullanmak için, aşağıdaki tabloda gösterildiği gibi, [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini ve [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabiriminin tüm yöntemlerini uygulamanız gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bir ifadeyi zaman uyumsuz olarak değerlendirir.|
|[Durdurulmaya](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz ifade değerlendirmesini sonlandırır.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bir ifadeyi zaman uyumlu olarak değerlendirir.|

 Zaman uyumlu ve zaman uyumsuz değerlendirme, [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodunu uygulamayı gerektirir. Zaman uyumsuz ifade değerlendirmesi, [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)uygulamasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
