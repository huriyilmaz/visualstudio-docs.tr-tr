---
title: İfade değerlendirici uygulama stratejisi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738674"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade değerlendirici uygulama stratejisi
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir ifade değerlendirici (EE) hızlı bir şekilde oluşturulmasına yönelik bir yaklaşım, yerel değişkenleri **Yereller** penceresinde göstermek için gereken en düşük kodu uygulamaktır. **Yereller** penceresindeki her bir satırın yerel bir değişkenin adını, türünü ve değerini görüntülediğini ve üçü de bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi tarafından temsil edileceğini fark etmek yararlı olur. Yerel bir değişkenin adı, türü ve değeri, `IDebugProperty2` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi çağırarak nesnesinden elde edilir. Yerel değişkenleri **Yereller** penceresinde görüntüleme hakkında daha fazla bilgi için bkz. [Locals görüntüleme](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Tartışma
 Olası bir uygulama sırası [ıdebugexpressiondeğerlendirici](../../extensibility/debugger/reference/idebugexpressionevaluator.md)uygulamayla başlar. Locals [ve](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemlerinin yerelleri görüntülemesi için uygulanması gerekir. Çağırma `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` bir yöntemi temsil eden bir nesne döndürür: Yani bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi. Yöntemler **Yereller** penceresinde görüntülenmez.

 Daha sonra [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemi uygulanmalıdır. Hata ayıklama altyapısı (DE), `IDebugProperty2::EnumChildren` bir bağımsız değişkeni geçirerek yerel değişkenlerin ve bağımsız değişkenlerin bir listesini almak için bu yöntemi çağırır `guidFilter` `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` sonuçları tek bir Numaralandırmadaki birleştiren [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [enumyereller](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)çağırır. Daha fazla ayrıntı için bkz. [yerel öğeleri görüntüleme](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Yerelleri görüntüle](../../extensibility/debugger/displaying-locals.md)
