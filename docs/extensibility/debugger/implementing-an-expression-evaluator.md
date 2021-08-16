---
title: Ifade Değerlendiricisi uygulama | Microsoft Docs
description: Hata ayıklama altyapısını, sembol sağlayıcısını, Ciltçi nesnesini ve ifade değerlendirici 'ni içeren bir ifadeyi değerlendirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4d4c5ab78d8a7d125bf78b32317bfeba673d7ef99852d69aab5e99bd6a59ee96
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361125"
---
# <a name="implement-an-expression-evaluator"></a>İfade değerlendiricisi uygulama
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir ifadeyi değerlendirmek, hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), Ciltçi nesnesi ve ifade değerlendirici (EE) arasında karmaşık bir karşılıklı yürütme işlemi olur. Bu dört bileşen, bir bileşen tarafından uygulanan ve başka bir bileşen tarafından tüketilen arabirimlere bağlanır.

 EE, bir dize biçimindeki öğesinden de bir ifade alır ve bunu ayrıştırır veya değerlendirir. EE, ve tarafından tüketilen aşağıdaki arayüzleri çalıştırır:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE, sembolleri ve nesnelerinin değerini almak için de tarafından sağlanan cilt nesnesini çağırır. EE, tarafından uygulanan aşağıdaki arayüzleri kullanır:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)çalışır. `IDebugProperty2`yerel değişken, temel öğe veya Visual Studio bir nesne gibi bir ifade değerlendirmesinin sonucunu açıklamak için mekanizma sağlar ve ardından **yereller**, **izle** veya **hemen** penceresinde uygun bilgileri görüntüler.

  SP, bilgi istediğinde DE EE tarafından verilir. SP, aşağıdaki arabirimler ve bunların türevleri gibi adresleri ve alanları tanımlayan arabirimler çalıştırır:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE, bu arabirimlerin tümünü tüketir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirici uygulama stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) ifade değerlendirici (EE) uygulama stratejisi için üç adımlı bir işlem tanımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
