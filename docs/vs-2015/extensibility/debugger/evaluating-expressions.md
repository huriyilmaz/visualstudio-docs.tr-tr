---
title: Ifadeleri değerlendirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151628"
---
# <a name="evaluating-expressions"></a>İfadeleri Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İfadeler, hızlı bir şekilde veya anında Windows 'tan geçirilen dizelerden oluşturulur. Bir ifade değerlendirildiğinde, değişken veya bağımsız değişkenin adını ve türünü ve değerini içeren yazdırılabilir bir dize oluşturur. Bu dize, karşılık gelen IDE penceresinde görüntülenir.  
  
## <a name="implementation"></a>Uygulama  
 Bir program kesme noktasında durdurulduğunda ifadeler değerlendirilir. İfadenin kendisi, verilen ifade değerlendirme bağlamı içinde bağlama ve değerlendirme için hazırlanma bir ayrıştırılmış ifadeyi temsil eden bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi tarafından temsil edilir. Yığın çerçevesi, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini uygulayarak hata ayıklama ALTYAPıSıNıN (de) sağladığı ifade değerlendirme bağlamını belirler.  
  
 Bir kullanıcı dizesi ve bir [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi verildiğinde, bir hata ayıklama ALTYAPıSı (de), Kullanıcı dizesini [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemine geçirerek bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi elde edebilir. Döndürülen IDebugExpression2 arabirimi, değerlendirme için Ready ayrıştırılmış ifadeyi içerir.  
  
 Arabirimi ile, `IDebugExpression2` [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)kullanarak ifadenin değerini zaman uyumlu veya zaman uyumsuz ifade değerlendirmesi aracılığıyla alabilir. Bu değer, değişkenin veya bağımsız değişkenin adı ve türü ile birlikte görüntülenmek üzere IDE 'ye gönderilir. Değer, ad ve tür bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi tarafından temsil edilir.  
  
 İfade değerlendirmesini etkinleştirmek için, bir DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ve [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimlerini uygulamalıdır. Hem zaman uyumlu hem de zaman uyumsuz değerlendirme, [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yönteminin uygulanmasını gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)   
 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)   
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)
