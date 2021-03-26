---
title: Yerelleri görüntüleme | Microsoft Docs
description: Her şey, Yürütme durakladığında görüntülenen yöntemin yerellerinin adı verilen yerel değişkenlerin ve bağımsız değişkenlerin listesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 564b42a15e1420027b79cb5f00c70f61649ad4f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097272"
---
# <a name="display-locals"></a>Yerelleri görüntüle
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Yürütme her zaman, kapsayan Yöntem veya geçerli yöntem olarak da bilinen bir yöntem bağlamı içinde gerçekleşir. Yürütme durakladığında, Visual Studio, her zaman yöntemin yerelleri olarak adlandırılan yerel değişkenlerin ve bağımsız değişkenlerin bir listesini almak için hata ayıklama altyapısını (DE) çağırır. Visual Studio bu yerelleri ve bunların değerlerini **Yereller** penceresinde görüntüler.

 Yerelleri göstermek için, EE 'a ait [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemini çağırır ve buna bir değerlendirme bağlamı, yani bir sembol sağlayıcısı (SP), geçerli yürütme adresi ve bir Ciltçi nesnesi verir. Daha fazla bilgi için bkz. [değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md). Çağrı başarılı olursa, `IDebugExpressionEvaluator::GetMethodProperty` yöntemi geçerli yürütme adresini içeren yöntemi temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

 Aynı şekilde, yalnızca Yereller döndürecek şekilde filtrelenmiş ve [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapılarının bir listesini oluşturmak için numaralandırılan bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesini almak için [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağrılır. Her yapı yerel değerin adını, türünü ve değerini içerir. Tür ve değer, görüntülenmek üzere uygun şekilde biçimlendirilen dizeler olarak depolanır. Ad, tür ve değer genellikle **Yereller** penceresinin tek bir satırında birlikte görüntülenir.

> [!NOTE]
> **QuickWatch** ve **Watch** pencereleri aynı ada, değere ve türe sahip değişkenleri de görüntüler. Ancak, bu değerler yerine [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) çağırarak elde edilir `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>Bu bölümde
 [Yereller Için örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md) Yerelleri uygulama sürecinde ilerlemek için örnekleri kullanır.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) Hata ayıklama altyapısı (DE), ifade değerlendirici (EE) çağırıyorsa, üç bağımsız değişken geçirdiği açıklanır.

## <a name="see-also"></a>Ayrıca bkz.
 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
