---
title: İfade Değerlendirici Nin Uygulanması | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738543"
---
# <a name="implement-an-expression-evaluator"></a>İfade değerlendiricisi uygulama
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bir ifadeyi değerlendirmek hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), bağlayıcı nesnesi ve ifade değerlendiricisi (EE) arasında karmaşık bir etkileşimdir. Bu dört bileşen, bir bileşen tarafından uygulanan ve başka bir bileşen tarafından tüketilen arabirimler tarafından bağlanır.

 EE bir dize şeklinde DE bir ifade alır ve parses veya değerlendirir. EE, DE tarafından tüketilen aşağıdaki arabirimleri çalıştırmaktadır:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE, sembollerin ve nesnelerin değerini almak için DE tarafından sağlanan bağlayıcı nesnesini çağırır. EE, DE tarafından uygulanan aşağıdaki arabirimleri tüketir:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)çalışır. `IDebugProperty2`yerel bir değişken, ilkel veya Visual Studio'ya bir nesne gibi bir ifade değerlendirmesinin sonucunu açıklayan mekanizmayı sağlar ve bu da yerel olarak uygun bilgileri **Yerel Olarak**, **İzle veya** **Hemen** penceresinde görüntüler.

  SP, bilgi istediğinde DE tarafından EE'ye verilir. SP, adresleri ve alanları açıklayan aşağıdaki arabirimler ve türevleri gibi arabirimler çalıştırMaktadır:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE tüm bu arabirimleri tüketir.

## <a name="in-this-section"></a>Bu bölümde
 [İfade değerlendirici uygulama stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) İfade değerlendiricisi (EE) uygulama stratejisi için üç aşamalı bir işlem tanımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
