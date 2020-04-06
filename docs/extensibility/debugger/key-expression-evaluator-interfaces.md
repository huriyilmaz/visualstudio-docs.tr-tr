---
title: Anahtar İfade Değerlendirici Arayüzleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738497"
---
# <a name="key-expression-evaluator-interfaces"></a>Anahtar ifade değerlendirici arabirimleri
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR ifade değerlendiricilerve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneğine](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bir ifade değerlendiricisi (EE) yazarken, değerlendirme bağlamı ile birlikte aşağıdaki arabirimleri bilmelidir.

## <a name="interface-descriptions"></a>Arayüz açıklamaları

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Geçerli yürütme noktasını temsil eden bir veri yapısı alan [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)adlı tek bir yöntemi vardır. Bu veri yapısı, hata ayıklama altyapısının (DE) bir ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) yöntemine geçtiği üç bağımsız değişkenden biridir. Bu arabirim genellikle sembol sağlayıcı tarafından uygulanır.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Bir sembolün geçerli değerini içeren bellek alanını alan [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemivardır. IDebugObject nesnesi tarafından temsil edilen içeren yöntem ve bir `IDebugBinder::Bind` [IDebugField](../../extensibility/debugger/reference/idebugobject.md) nesnesi tarafından temsil edilen sembolün kendisi göz önüne alındığında, sembolün değerini döndürür. [IDebugField](../../extensibility/debugger/reference/idebugfield.md) `IDebugBinder`genellikle DE tarafından uygulanır.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Basit bir veri türünü temsil eder. Diziler ve yöntemler gibi daha karmaşık türler için sırasıyla türetilmiş [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) ve [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimlerini kullanın. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) yöntemleri veya sınıflar gibi diğer semboller içeren sembolleri temsil eden başka bir önemli türemiş arabirimdir. `IDebugField` Arabirim (ve türevleri) genellikle sembol sağlayıcı tarafından uygulanır.

     Bir `IDebugField` nesne, bir sembolün adını ve türünü bulmak için kullanılabilir ve bir [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) nesnesi ile birlikte değerini bulmak için kullanılabilir.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Bir sembolün çalışma zamanı değerinin gerçek bitlerini temsil eder. [Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) bir simgeyi temsil eden bir [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesini alır ve bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesini döndürür. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) yöntemi, bellek arabelleğindeki sembolün değerini döndürür. DE genellikle bellekte bir özelliğin değerini temsil etmek için bu arabirimi uygular.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Bu arabirim ifade değerlendiricinin kendisini temsil eder. Anahtar yöntem [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi döndürür.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Bu arabirim, değerlendirilmeye hazır ayrışmış bir ifadeyi temsil eder. Anahtar yöntem, ifadenin değerini ve türünü temsil eden bir IDebugProperty2 döndüren [EvaluateSync'dir.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Bu arabirim bir değeri ve türünü temsil eder ve bir ifade değerlendirmesinin sonucudur.

## <a name="see-also"></a>Ayrıca bkz.
- [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)
