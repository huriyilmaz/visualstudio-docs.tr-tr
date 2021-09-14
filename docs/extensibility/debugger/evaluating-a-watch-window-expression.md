---
title: Gözcü penceresi Ifadesi hesaplanıyor | Microsoft Docs
description: yürütme durakladığında, izleme listesindeki her bir ifadenin geçerli değerini öğrenmek için Visual Studio hata ayıklama altyapısını nasıl çağırdığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fbd9ad916b034158f21f909d9895629db74e0718
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627650"
---
# <a name="evaluate-a-watch-window-expression"></a>Gözcü penceresi ifadesini değerlendir
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 yürütme durakladığında, Visual Studio, izleme listesindeki her bir ifadenin geçerli değerini belirlemekte hata ayıklama altyapısını (DE) çağırır. , her ifadeyi bir ifade değerlendirici (EE) kullanarak değerlendirir ve Visual Studio, **izleme** penceresinde değerini görüntüler.

 Aşağıda, bir izleme listesi ifadesinin nasıl değerlendirildiğini gösteren bir genel bakış verilmiştir:

1. Visual Studio, ifadeleri değerlendirmek için kullanılabilecek bir ifade bağlamı almak için DE ' ın [getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ' i çağırır.

2. izleme listesindeki her bir ifade için, Visual Studio ifade metnini ayrıştırılmamış bir ifadeye dönüştürmek için [parsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 'i çağırır.

3. `IDebugExpressionContext2::ParseText`metni ayrıştırmanın gerçek işini yapmak ve bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesi üretmek için [ayrıştırmayı](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır.

4. `IDebugExpressionContext2::ParseText` bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi oluşturur ve `IDebugParsedExpression` nesneyi buna koyar. `DebugExpression2`Daha sonra bu i nesnesi Visual Studio döndürülür.

5. Visual Studio ayrıştırılmış ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır.

6. `IDebugExpression2::EvaluateSync`gerçek değerlendirmeyi yapmak ve Visual Studio döndürülen bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi oluşturmak için [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrısını geçirir.

7. Visual Studio, daha sonra izleme listesinde görüntülenen ifadenin değerini almak için [getpropertyınfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) öğesini çağırır.

## <a name="parse-then-evaluate"></a>Ayrıştırmaya sonra değerlendir
 Karmaşık bir ifadenin ayrıştırılması, hesaplanmasından çok daha uzun sürebileceğinden, bir ifadeyi değerlendirme işlemi iki adımda ayrılır: 1) ifadeyi ayrıştırır ve 2) ayrıştırılmış ifadeyi değerlendirin. Bu şekilde, değerlendirme birçok kez gerçekleşebilir, ancak ifadenin yalnızca bir kez ayrıştırılabilmesi gerekir. ara ayrıştırılmış ifade, sırasıyla kapsüllenmiş ve bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi olarak döndürülen bir [ıdebugparsedexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesindeki EE döndürülür. `IDebugExpression`Nesnesi, nesnesine tüm değerlendirmeyi erteler `IDebugParsedExpression` .

> [!NOTE]
> EE, bu iki adımlı işleme uyması için gerekli değildir; ancak bu, Visual Studio bunu varsaysa da, EE, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrıldığında aynı adımda ayrıştırılabilir ve değerlendirebilir (örneğin, mycee örneğinin çalışma biçimi). Diliniz karmaşık ifadeler oluştursa, değerlendirme adımından ayrıştırma adımını ayırmak isteyebilirsiniz. bu, çok sayıda izleme ifadesi gösterildiğinde Visual Studio hata ayıklayıcıda performansı artırabilir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirmesinin örnek uygulama](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) , İfade değerlendirmesi sürecinde ilerlemek için MyCEE örneğini kullanır.

 [Bir gözcü Ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md) Başarılı bir ifade ayrıştırdıktan sonra ne olacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) Hata ayıklama altyapısı (DE), ifade değerlendirici (EE) çağırdığında geçirilen bağımsız değişkenleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.
 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
