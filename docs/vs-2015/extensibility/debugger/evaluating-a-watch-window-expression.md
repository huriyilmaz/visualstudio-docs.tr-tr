---
title: Gözcü penceresi Ifadesi hesaplanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820427"
---
# <a name="evaluating-a-watch-window-expression"></a>Gözcü Penceresi İfadesini Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Yürütme duraklatıldığında, Visual Studio, izleme listesindeki her bir ifadenin geçerli değerini öğrenmek için hata ayıklama altyapısını (DE) çağırır. , Her ifadeyi bir ifade değerlendirici (EE) kullanarak değerlendirir ve Visual Studio bu değeri **Gözcü** penceresinde görüntüler.  
  
 Aşağıda, bir izleme listesi ifadesinin nasıl değerlendirildiğini gösteren bir genel bakış verilmiştir:  
  
1. Visual Studio, ifadeleri değerlendirmek için kullanılabilecek bir ifade bağlamı almak için DE DE [Getexpressionbağlamını](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) çağırır.  
  
2. İzleme listesindeki her bir ifade için, Visual Studio, ifade metnini ayrıştırılabilen bir ifadeye dönüştürmek için [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 'i çağırır.  
  
3. `IDebugExpressionContext2::ParseText`metni ayrıştırmanın gerçek işini yapmak ve bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesi üretmek için [ayrıştırmayı](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır.  
  
4. `IDebugExpressionContext2::ParseText` bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi oluşturur ve `IDebugParsedExpression` nesneyi buna koyar. Bu I `DebugExpression2` nesnesi daha sonra Visual Studio 'ya döndürülür.  
  
5. Visual Studio, ayrıştırılmış ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır.  
  
6. `IDebugExpression2::EvaluateSync`[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrısını, gerçek değerlendirmeyi yapmak ve Visual Studio 'ya döndürülen bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi üretmek için geçirir.  
  
7. Visual Studio, daha sonra izleme listesinde görüntülenen ifadenin değerini almak için [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) çağırır.  
  
## <a name="parse-then-evaluate"></a>Ayrıştırmaya sonra değerlendir  
 Karmaşık bir ifadenin ayrıştırılması, hesaplanmasından çok daha uzun sürebileceğinden, bir ifadeyi değerlendirme işlemi iki adımda ayrılır: 1) ifadeyi ayrıştırır ve 2) ayrıştırılmış ifadeyi değerlendirin. Bu şekilde, değerlendirme birçok kez gerçekleşebilir, ancak ifadenin yalnızca bir kez ayrıştırılabilmesi gerekir. Ara ayrıştırılmış ifade, sırasıyla kapsüllenmiş ve bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi olarak döndürülen bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesindeki Ee öğesinden döndürülür. `IDebugExpression`Nesnesi, nesnesine tüm değerlendirmeyi erteler `IDebugParsedExpression` .  
  
> [!NOTE]
> Visual Studio bunu varsaysa da, bir EE 'nin bu iki adımlı işleme uyması gerekmez; EE, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrıldığında aynı adımda ayrıştırılabilir ve değerlendirebilir (örneğin, MyCEE örneğinin çalışma biçimi). Diliniz karmaşık ifadeler oluştursa, değerlendirme adımından ayrıştırma adımını ayırmak isteyebilirsiniz. Birçok izleme ifadesi gösterildiğinde bu, Visual Studio hata ayıklayıcısında performansı artırabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Örnek İfade Değerlendirme Uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 , İfade değerlendirmesi sürecinde ilerlemek için MyCEE örneğini kullanır.  
  
 [Bir Gözcü İfadesini Değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Başarılı bir ifade ayrıştırdıktan sonra ne olacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)  
 Hata ayıklama altyapısı (DE), ifade değerlendirici (EE) çağırdığında geçirilen bağımsız değişkenleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
