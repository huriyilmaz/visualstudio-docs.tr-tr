---
title: İfade Değerlendirici Mimari | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738703"
---
# <a name="expression-evaluator-architecture"></a>İfade değerlendirici mimarisi
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Özel bir dili Visual Studio hata ayıklama paketine entegre etmek, gerekli ifade değerlendirici (EE) arabirimlerini ayarlamanız ve ortak dil çalışma zamanı sembol sağlayıcısını (SP) ve bağlayıcı arabirimlerini aramanız gerektiği anlamına gelir. SP ve bağlayıcı nesneleri, geçerli yürütme adresiyle birlikte, ifadelerin değerlendirildiği bağlamdır. Bu arabirimlerin ürettiği ve tükettiği bilgiler, bir EE mimarisindeki temel kavramları temsil eder.

## <a name="overview"></a>Genel Bakış

### <a name="parse-the-expression"></a>İfadeyi Ayrışdır
 Bir programı hata ayıklarken, ifadeler bir dizi nedenden dolayı değerlendirilir, ancak her zaman hata ayıklanan program bir kesme noktasında durdurulduğunda (kullanıcı tarafından yerleştirilen bir kesme noktası veya özel bir özel durum nedeniyle bir kesme noktası). Visual Studio hata ayıklama motoru (DE) [iDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arayüzü tarafından temsil edildiği gibi, bir yığın çerçeve elde bu anda. Visual Studio daha sonra [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini almak için [GetExpressionContext'ı](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) arar. Bu arabirim, ifadelerin değerlendirilebileceği bir bağlamı temsil eder; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) değerlendirme sürecinin giriş noktasıdır. Bu noktaya kadar, tüm arabirimler DE tarafından uygulanır.

 Çağrıldığında, `IDebugExpressionContext2::ParseText` DE kesme noktasının oluştuğu kaynak dosyanın diliyle ilişkili EE'yi anında alar (DE de bu noktada SH'yi anında anında işareteder). EE, [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi ile temsil edilir. DE daha sonra [parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ifadesini (metin biçiminde) ayrıştırılmış bir ifadeye dönüştürmek için çağırır, değerlendirmeye hazır. Bu ayrıştırılmış ifade [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi tarafından temsil edilir. İfade genellikle ayrıştırılır ve bu noktada değerlendirilmez.

 DE, [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan, `IDebugParsedExpression` nesneyi `IDebugExpression2` nesneye koyan ve nesneyi `IDebugExpression2` `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>İfadeyi değerlendirme
 Visual Studio, ayrışmış ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync'i](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) çağırır. Bu yöntemlerin her ikisi`IDebugExpression2::EvaluateSync` de ayrıştırılmış ifadeyi değerlendirmek ve ayrıştırılmış ifadenin değerini ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini döndürmek için [EvaluateSync'i](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (yöntemi hemen çağırırken, `IDebugExpression2::EvaluateAsync` yöntemi arka plan iş parçacığı üzerinden çağırır) çağırır. `IDebugParsedExpression::EvaluateSync`verilen SH, adresi ve bağlayıcıyı, ayrıştı ifadesini `IDebugProperty2` arabirim tarafından temsil edilen gerçek bir değere dönüştürmek için kullanır.

### <a name="for-example"></a>Örneğin:
 Çalışan bir programda bir kesme noktası vurulduktan sonra, kullanıcı **QuickWatch** iletişim kutusunda bir değişkengörüntülemeyi seçer. Bu iletişim kutusu değişkenin adını, değerini ve türünü gösterir. Kullanıcı genellikle değeri değiştirebilir.

 **QuickWatch** iletişim kutusu gösterildiğinde, incelenen değişkenin adı [ParseText'e](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)metin olarak gönderilir. Bu, ayrışmış ifadeyi temsil eden bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi döndürür, bu durumda, değişken. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) sonra değişkenin `IDebugProperty2` değerini ve türünü yanı sıra adını temsil eden bir nesne üretmek için çağrılır. Görüntülenen bu bilgilerdir.

 Kullanıcı değişkenin değerini değiştirirse, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) yeni değerle birlikte çağrılır ve bu değer bellekteki değişkenin değerini değiştirir, böylece program çalışmaya devam ettiğinde kullanılacaktır.

 Bkz. Değişkenlerin değerlerini görüntüleme işlemi hakkında daha fazla ayrıntı için [yerel verileri](../../extensibility/debugger/displaying-locals.md) görüntüleme. Bkz. Bir değişkenin değerinin nasıl değiştirilme şekli hakkında daha fazla bilgi için yerel bir [yerin değerini](../../extensibility/debugger/changing-the-value-of-a-local.md) değiştirme.

## <a name="in-this-section"></a>Bu bölümde
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) DE EE'yi aradığında geçirilen bağımsız değişkenleri sağlar.

 [Anahtar ifade değerlendirici arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md) EE yazarken gereken önemli arabirimleri ve değerlendirme bağlamını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Yerel halkların görüntülenmesi](../../extensibility/debugger/displaying-locals.md)
- [Yerel bir değer değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md)
