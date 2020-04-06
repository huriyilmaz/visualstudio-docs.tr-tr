---
title: İfade Değerlendirici Uygulama Stratejisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738674"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade değerlendirici uygulama stratejisi
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Hızla bir ifade değerlendirici (EE) oluşturmak için bir yaklaşım ilk **Yereller** penceresinde yerel değişkenleri görüntülemek için gerekli minimum kodu uygulamaktır. **Yerel aygıtlar** penceresindeki her satırın yerel bir değişkenin adını, türünü ve değerini görüntülediğini ve üçünün de bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi tarafından temsil edildiğini fark etmek yararlıdır. Yerel bir değişkenin adı, türü ve `IDebugProperty2` [değeri, getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemini çağırarak bir nesneden elde edilir. **Yerel değişkenlerin Yerel ler** penceresinde nasıl görüntülenebilenhakkında daha fazla bilgi için bkz. [Displaying locals](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>Tartışma
 Olası bir uygulama sırası [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)uygulanması ile başlar. Yerel halkları görüntülemek için [Ayrıştırık](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ve [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemleri uygulanmalıdır. Arama, `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` bir yöntemi temsil eden bir nesneyi döndürür: yani bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi. Yöntemlerin kendileri Yerel **ler** penceresinde görüntülenmez.

 Daha sonra [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemi uygulanmalıdır. Hata ayıklama altyapısı (DE) bir `IDebugProperty2::EnumChildren` `guidFilter` bağımsız değişken ilerleyerek yerel değişkenlerin `guidFilterLocalsPlusArgs`ve bağımsız değişkenlerin listesini almak için bu yöntemi çağırır. `IDebugProperty2::EnumChildren`[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)çağırır , tek bir numaralandırma sonuçları birleştirerek. Daha fazla ayrıntı için [yerel verileri görüntüle'ye](../../extensibility/debugger/displaying-locals.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Yerel leri görüntüleyin](../../extensibility/debugger/displaying-locals.md)
