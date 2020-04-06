---
title: İfadeleri Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738833"
---
# <a name="evaluate-expressions"></a>İfadeleri değerlendirme
**İfadeler, Otomatik Olarak**, **İzle,** **QuickWatch**veya **Hemen** pencerelerinden geçirilen dizeleri oluşturulur. Bir ifade değerlendirildiğinde, değişken veya bağımsız değişkenin adını ve türünü ve değerini içeren yazdırılabilir bir dize oluşturur. Bu dize ilgili IDE penceresinde görüntülenir.

## <a name="implementation"></a>Uygulama
 Bir program bir kesme noktasında durdurulduğunda ifadeler değerlendirilir. İfadenin kendisi, verilen ifade değerlendirme bağlamında bağlama ve değerlendirmeye hazır ayrıştırılmış bir ifadeyi temsil eden bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi yle temsil edilir. Yığın çerçevesi, Hata Ayıklama altyapısının (DE) [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini uygulayarak sağladığı ifade değerlendirme bağlamını belirler.

 Bir kullanıcı dizesi ve [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi göz önüne alındığında, hata ayıklama altyapısı (DE) kullanıcı dizesini [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemine geçirerek bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi elde edebilir. Döndürülen IDebugExpression2 arabirimi, değerlendirmeye hazır ayrışmış ifadeyi içerir.

 `IDebugExpression2` Arabirim ile DE, [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)kullanarak senkron veya eşzamanlı ifade değerlendirmesi yoluyla ifadenin değerini alabilir. Bu değer, değişken in adı ve türü yle birlikte görüntülenmek üzere IDE'ye gönderilir. Değer, ad ve tür bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi yle temsil edilir.

 İfade değerlendirmesini etkinleştirmek için, bir [DE'nin IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ve [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimlerini uygulaması gerekir. Hem senkron hem de eşzamanlı [değerlendirme, IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yönteminin uygulanmasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
