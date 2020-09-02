---
title: Anahtar Ifade değerlendirici arabirimleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9c01c59e732b777967cf49a61f17305f666325f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805687"
---
# <a name="key-expression-evaluator-interfaces"></a>Anahtar İfade Değerlendiricisi Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bir ifade değerlendirici (EE) yazarken, değerlendirme bağlamıyla birlikte aşağıdaki arabirimlere tanıdık gelmelidir.  
  
## <a name="interface-descriptions"></a>Arabirim açıklamaları  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     , Geçerli yürütme noktasını temsil eden bir veri yapısını alan [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)tek bir yöntemine sahiptir. Bu veri yapısı, hata ayıklama altyapısının (DE) bir ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) yöntemine geçirdiği üç bağımsız değişkenlerden biridir. Bu arabirim genellikle sembol sağlayıcısı tarafından uygulanır.  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     , Bir simgenin geçerli değerini içeren bellek alanını alan [bind](../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemine sahiptir. Hem bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesi tarafından temsil edilen hem de bir [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesi tarafından temsil edilen sembol kendisini içeren kapsayan yöntemi verildiğinde, `IDebugBinder::Bind` simgenin değerini döndürür. `IDebugBinder` genellikle DE ile uygulanır.  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Basit bir veri türünü temsil eder. Diziler ve yöntemler gibi daha karmaşık türler için sırasıyla türetilmiş [ıdebuggarrayfield](../../extensibility/debugger/reference/idebugarrayfield.md) ve [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimlerini kullanın. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , Yöntemler veya sınıflar gibi diğer sembolleri içeren sembolleri temsil eden başka bir önemli türetilmiş arabirimdir. `IDebugField`Arabirim (ve türetmesinin), genellikle sembol sağlayıcısı tarafından uygulanır.  
  
     Bir `IDebugField` nesne, bir simgenin adını ve türünü bulmak için ve bir [ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md) nesnesiyle birlikte, değerini bulmak için kullanılabilir.  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Bir simgenin çalışma zamanı değerinin gerçek bitlerini temsil eder. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) bir sembolü temsil eden bir [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesi alır ve bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesi döndürür. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) yöntemi, bir bellek arabelleğindeki simgenin değerini döndürür. Bu, tipik olarak bu arabirimi, bellekteki bir özelliğin değerini temsil etmek için uygular.  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Bu arabirim, ifade değerlendiricisi kendisini temsil eder. Anahtar yöntemi bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimini döndüren [ayrıştırmaktır](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Bu arabirim, değerlendirilen bir ayrıştırılmış ifadeyi temsil eder. Key yöntemi, ifadenin değerini ve türünü temsil eden bir IDebugProperty2 döndüren [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) .  
  
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Bu arabirim bir değeri ve türünü temsil eder ve bir ifade değerlendirmesinin sonucudur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)
