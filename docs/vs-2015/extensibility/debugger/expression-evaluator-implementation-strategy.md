---
title: İfade değerlendirici uygulama stratejisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824696"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade Değerlendiricisi Uygulama Stratejisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bir ifade değerlendirici (EE) hızlı bir şekilde oluşturulmasına yönelik bir yaklaşım, yerel değişkenleri **Yereller** penceresinde göstermek için gereken en düşük kodu uygulamaktır. **Yereller** penceresindeki her bir satırın yerel bir değişkenin adını, türünü ve değerini görüntülediğini ve üçü de bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi tarafından temsil edileceğini fark etmek yararlı olur. Bir yerel değişkenin adı, türü ve değeri, `IDebugProperty2` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi çağırarak bir nesneden elde edilebilir. Yerel değişkenleri **Yereller** penceresinde görüntüleme hakkında daha fazla bilgi için bkz. [Locals görüntüleme](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Tartışma  
 Olası bir uygulama sırası [ıdebugexpressiondeğerlendirici](../../extensibility/debugger/reference/idebugexpressionevaluator.md)uygulamayla başlar. Yerelleri göstermek için [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ve [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemlerinin uygulanması gerekir. Çağırma `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` bir yöntemi temsil eden bir nesne döndürür: Yani bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi. Yöntemler **Yereller** penceresinde görüntülenmez.  
  
 Daha sonra [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemi uygulanmalıdır. Hata ayıklama altyapısı (DE), `IDebugProperty2::EnumChildren` bir bağımsız değişkeni geçirerek yerel değişkenlerin ve bağımsız değişkenlerin bir listesini almak için bu yöntemi çağırır `guidFilter` `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` sonuçları tek bir Numaralandırmadaki birleştiren [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [enumyereller](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)çağırır. Daha fazla ayrıntı için bkz. [Locals görüntüleme](../../extensibility/debugger/displaying-locals.md) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ifade Değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Yerel Öğeleri Görüntüleme](../../extensibility/debugger/displaying-locals.md)
