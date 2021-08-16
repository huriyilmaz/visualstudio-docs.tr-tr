---
title: Anahtar İfade Değerlendirici Arabirimleri | Microsoft Docs
description: Bir ifade değerlendiricisi yazarken tanımanız gereken arabirimleri ve değerlendirme bağlamını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c9f484b485910b6fd10cec24863f89f0a49de92c6933ab8fcd62427f948b995b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361086"
---
# <a name="key-expression-evaluator-interfaces"></a>Anahtar ifadesi değerlendirici arabirimleri
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bir ifade değerlendiricisi (EE) yazarken, değerlendirme bağlamıyla birlikte aşağıdaki arabirimlere aşina olmak gerekir.

## <a name="interface-descriptions"></a>Arabirim açıklamaları

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Geçerli yürütme noktasını temsil eden bir veri yapısını alan tek bir [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)yöntemi vardır. Bu veri yapısı, hata ayıklama altyapısının (DE) bir ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) yöntemine geçtiği üç bağımsız değişkenden biridir. Bu arabirim genellikle sembol sağlayıcısı tarafından uygulanır.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Bir [sembolün](../../extensibility/debugger/reference/idebugbinder-bind.md) geçerli değerini içeren bellek alanı alan Bind yöntemine sahiptir. Bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesiyle temsil edilen içeren yöntemin ve [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesiyle temsil edilen sembolün kendisi, `IDebugBinder::Bind` sembolün değerini döndürür. `IDebugBinder` genellikle DE tarafından uygulanır.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Basit bir veri türünü temsil eder. Diziler ve yöntemler gibi daha karmaşık türler için sırasıyla türetilmiş [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) ve [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimlerini kullanın. [IDebugContainerField,](../../extensibility/debugger/reference/idebugcontainerfield.md) yöntemler veya sınıflar gibi diğer sembolleri içeren sembolleri temsil eden başka bir önemli türetilmiş arabirimdir. Arabirim `IDebugField` (ve türevleri) genellikle sembol sağlayıcısı tarafından uygulanır.

     Bir nesne, bir sembolün adını ve türünü bulmak için ve değerini bulmak `IDebugField` için [bir IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) nesnesiyle birlikte kullanılabilir.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Bir sembolün çalışma zamanı değerinin gerçek bitlerini temsil eder. [Bağlama,](../../extensibility/debugger/reference/idebugbinder-bind.md) bir [simgeyi temsil eden bir IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesini alır ve [bir IDebugObject nesnesi](../../extensibility/debugger/reference/idebugobject.md) döndürür. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) yöntemi, bellek arabelleğinde sembol değerini döndürür. DE genellikle bellekte bir özelliğin değerini temsil etmek için bu arabirimi kullanır.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Bu arabirim ifade değerlendiricinin kendisini temsil eder. Anahtar yöntem, [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimini döndüren [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)yöntemidir.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Bu arabirim, değerlendirilmeye hazır ayrıştırmış bir ifadeyi temsil eder. Anahtar yöntem, [ifadenin değerini](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ve türünü temsil eden bir IDebugProperty2 döndüren EvaluateSync yöntemidir.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Bu arabirim bir değeri ve türünü temsil eder ve ifade değerlendirmesinin sonucu olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)
