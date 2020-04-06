---
title: Saat Penceresi İfadesini Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738844"
---
# <a name="evaluate-a-watch-window-expression"></a>Saat penceresi ifadesini değerlendirme
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Yürütme duraklatıldığında, Visual Studio izleme listesindeki her ifadenin geçerli değerini belirlemek için hata ayıklama altyapısını (DE) çağırır. DE her ifadeyi bir ifade değerlendiricisi (EE) kullanarak değerlendirir ve Visual Studio değerini **İzleme** penceresinde görüntüler.

 İzleme listesi ifadesinin nasıl değerlendirildiğinin genel bir özeti aşağıda veda edilmiştir:

1. Visual Studio, ifadeleri değerlendirmek için kullanılabilecek bir ifade bağlamı almak için DE'nin [GetExpressionContext'ını](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) çağırır.

2. İzleme listesindeki her ifade için Visual Studio, ifade metnini ayrışmış bir ifadeye dönüştürmek için [ParseText'i](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağırır.

3. `IDebugExpressionContext2::ParseText`[parse'yi](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metni ayrışdırma fiili işini yapmaya ve bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesi oluşturmaya çağırır.

4. `IDebugExpressionContext2::ParseText`bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi `IDebugParsedExpression` oluşturur ve nesneyi içine koyar. Bu`DebugExpression2` i nesne sonra Visual Studio döndürülür.

5. Visual Studio, ayrıştı ifadesini değerlendirmek için [EvaluateSync'i](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır.

6. `IDebugExpression2::EvaluateSync`Gerçek değerlendirmeyi yapmak ve Visual Studio'ya döndürülen bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi üretmek için [EvaluateSync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrıyı geçirir.

7. Visual Studio, daha sonra izleme listesinde görüntülenen ifadenin değerini elde etmek için [GetPropertyInfo'yu](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) arar.

## <a name="parse-then-evaluate"></a>Ayrışdırın sonra değerlendirmek
 Karmaşık bir ifadeyi ayrıştırma, ifadeyi değerlendirmekten çok daha uzun sürebilir, bir ifadeyi değerlendirme işlemi iki adıma ayrılır: 1) ifadeyi ayrıştırma ve 2) ayrıştırılmış ifadeyi değerlendirir. Bu şekilde, değerlendirme birçok kez oluşabilir, ancak ifadenin yalnızca bir kez ayrıştırılması gerekir. Ara ayrıştırılmış ifade, sırayla kapsüllenen ve DE'den [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi olarak döndürülen bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde EE'den döndürülür. Nesne `IDebugExpression` tüm değerlendirmeyi `IDebugParsedExpression` nesneye erteler.

> [!NOTE]
> Visual Studio bunu kabul etse de, bir EE'nin bu iki aşamalı sürece uyması gerekli değildir; EE, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrıldığında aynı adımda ayrıştırabilir ve değerlendirebilir (örneğin MyCEE örneği bu şekilde çalışır). Diliniz karmaşık ifadeler oluşturabiliyorsa, ayrıştırman adımını değerlendirme adımından ayırmak isteyebilirsiniz. Bu, birçok saat ifadesi gösterildiğinde Visual Studio hata ayıklamaperformansı artırabilir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirmesinin örnek uygulanması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) İfade değerlendirme işleminde adım atmak için MyCEE örneğini kullanır.

 [Saat ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md) Başarılı bir ifade ayrıştisi sonra ne olur açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) Hata ayıklama altyapısı (DE) ifade değerlendiricisi (EE) çağırdığında geçirilen bağımsız değişkenleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.
 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
