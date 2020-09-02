---
title: İfade değerlendirmesi (Visual Studio hata ayıklama SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562217"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade Değerlendirme (Visual Studio Hata Ayıklama SDK’sı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kesme modu sırasında IDE, programınızın çeşitli değişkenlerini kapsayan basit ifadeleri değerlendirebilmelidir. Bunu gerçekleştirmek için, hata ayıklama altyapısı (DE), IDE 'nin bir pencerelerinin birine girilen bir ifadeyi ayrıştırabilmelidir ve değerlendirebilmelidir.  
  
 İfadeler [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak oluşturulur ve sonuçta elde edilen [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimiyle temsil edilir.  
  
 **IDebugExpression2** arabirimi de tarafından UYGULANıR ve IDE 'de ifade değerlendirmesinin sonuçlarını göstermek için **EVALASYNC** yöntemini çağırarak IDE 'ye bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , bir ifadenin değerini bir Izleme penceresi veya Locals penceresine koymak için kullanılabilecek bir yapı döndürür.  
  
 Hata ayıklama paketi veya oturum hata ayıklama Yöneticisi (SDM), değerlendirmenin sonucunu temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi almak için [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır. `IDebugProperty2` ifadenin adını, türünü ve değerini döndüren yöntemlere sahiptir. Bu bilgiler çeşitli hata ayıklayıcı pencereleri içinde görüntülenir.  
  
## <a name="using-expression-evaluation"></a>Ifade değerlendirmesini kullanma  
 İfade değerlendirmesini kullanmak için, aşağıdaki tabloda gösterildiği gibi, [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini ve [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabiriminin tüm yöntemlerini uygulamanız gerekir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bir ifadeyi zaman uyumsuz olarak değerlendirir.|  
|[Durdurulmaya](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz ifade değerlendirmesini sonlandırır.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bir ifadeyi zaman uyumlu olarak değerlendirir.|  
  
 Zaman uyumlu ve zaman uyumsuz değerlendirme, [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yönteminin uygulanmasını gerektirir. Zaman uyumsuz ifade değerlendirmesi, [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)uygulamasını gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme Denetimi ve Durum Değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
