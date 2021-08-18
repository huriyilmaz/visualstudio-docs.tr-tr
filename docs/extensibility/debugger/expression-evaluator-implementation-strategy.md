---
title: İfade Değerlendirici Uygulama Stratejisi | Microsoft Docs
description: İlk olarak Yereller penceresinde yerel değişkenleri görüntülemek için kod uygulayarak bir ifade değerlendiricisi oluşturma stratejisi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0c2b90f0101fe31c3f729006793330556186ddba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153503"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade değerlendiricisi uygulama stratejisi
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Hızlı bir şekilde ifade değerlendiricisi (EE) oluşturmaya yönelik yaklaşımlardan biri, yerel değişkenleri YerelLer penceresinde görüntülemek için gereken en düşük **kodu uygulamaktır.** YerelLer penceresindeki her satırın  yerel değişkenin adını, türünü ve değerini görüntüleyenin ve üçünün de [bir IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesiyle temsil edildiklerini fark etmek yararlıdır. Yerel değişkenin adı, türü ve değeri, `IDebugProperty2` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi çağrılarak bir nesneden elde edilir. Yerel değişkenler penceresinde yerel değişkenleri görüntüleme hakkında daha fazla **bilgi için** bkz. Yerel [değişkenleri görüntüleme.](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>Tartışma
 Olası bir uygulama [sırası, IDebugExpressionEvaluator uygulamayla başlar.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Yerelleri görüntülemek için [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ve [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemlerinin uygulanması gerekir. çağrısı `IDebugExpressionEvaluator::GetMethodProperty` yöntemi temsil eden bir nesne `IDebugProperty2` döndürür: yani bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesi. Yöntemlerin kendileri YerelLer **penceresinde görüntülenmez.**

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yönteminin bir sonraki adımında uygulanması gerekir. Hata ayıklama altyapısı (DE), bir bağımsız değişkeni geçerek yerel değişkenlerin ve bağımsız değişkenlerin listesini almak için `IDebugProperty2::EnumChildren` bu `guidFilter` yöntemi `guidFilterLocalsPlusArgs` çağırıyor. `IDebugProperty2::EnumChildren` , sonuçları tek bir numarayla birleştirerek [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [EnumLocals'ı](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)çağırıyor. Daha [fazla ayrıntı için bkz.](../../extensibility/debugger/displaying-locals.md) Yerelleri görüntüleme.

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)
