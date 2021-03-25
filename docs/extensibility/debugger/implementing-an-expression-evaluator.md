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
ms.workload:
- vssdk
ms.openlocfilehash: 7caee7b58f77f1b4e3f120f27ae076b438bedc63
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059879"
---
# <a name="implement-an-expression-evaluator"></a>İfade değerlendiricisi uygulama
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir ifadeyi değerlendirmek, hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), Ciltçi nesnesi ve ifade değerlendiricisi (EE) arasında karmaşık bir karşılıklı yürütme işlemi olur. Bu dört bileşen, bir bileşen tarafından uygulanan ve başka bir bileşen tarafından tüketilen arabirimlere bağlanır.

 EE, bir dize biçimindeki öğesinden DE bir ifade alır ve bunu ayrıştırır veya değerlendirir. EE, DE tarafından tüketilen aşağıdaki arayüzleri çalıştırır:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE, sembol ve nesne değerlerini almak için DE tarafından sağlanan cilt nesnesini çağırır. EE, ve tarafından uygulanan aşağıdaki arayüzleri kullanır:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE, [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)çalıştırır. `IDebugProperty2` Yerel bir değişken, temel öğe veya Visual Studio için bir nesne gibi bir ifade değerlendirmesinin sonucunu açıklamak için mekanizmayı sağlar ve ardından **Yereller**, **İzle** veya **hemen** penceresinde uygun bilgileri görüntüler.

  SP, bilgi istediğinde DE Bu, EE 'a verilir. SP, aşağıdaki arabirimler ve bunların türevleri gibi adresleri ve alanları tanımlayan arabirimler çalıştırır:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE bu arabirimlerin tümünü tüketir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirici uygulama stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) İfade değerlendirici (EE) uygulama stratejisi için üç adımlı bir işlem tanımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
