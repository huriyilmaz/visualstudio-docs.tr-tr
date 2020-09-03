---
title: Ifade Değerlendiricisi uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738543"
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

  EE, [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)çalıştırır. `IDebugProperty2` Yerel bir değişken, temel öğe veya Visual Studio için bir nesne gibi bir ifade değerlendirmesinin sonucunu açıklamak için mekanizmayı sağlar ve ardından **Yereller**, **İzle**veya **hemen** penceresinde uygun bilgileri görüntüler.

  SP, bilgi istediğinde DE Bu, EE 'a verilir. SP, aşağıdaki arabirimler ve bunların türevleri gibi adresleri ve alanları tanımlayan arabirimler çalıştırır:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE bu arabirimlerin tümünü tüketir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirici uygulama stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) İfade değerlendirici (EE) uygulama stratejisi için üç adımlı bir işlem tanımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
