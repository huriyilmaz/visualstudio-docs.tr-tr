---
title: YerelLeri Görüntüleme | Microsoft Docs
description: Yürütme duraklatılırken görüntülenen yönteminin yerel değerleri olarak adlandırılan yerel değişkenlerin ve bağımsız değişkenlerin listesi hakkında bilgi öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1b4ca685031f33198a0c9aedb7f9ea8c031f05b6af0e3531fb423aca986fab9c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343252"
---
# <a name="display-locals"></a>Yerelleri görüntüleme
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Yürütme her zaman, içeren yöntem veya geçerli yöntem olarak da bilinen bir yöntem bağlamında sürer. Yürütme duraklatılırken, Visual Studio yerel değişkenlerin ve bağımsız değişkenlerin listesini topluca yöntemin yerelleri olarak adlandırılan bir listesini almak için hata ayıklama altyapısını (DE) çağırabilirsiniz. Visual Studio yerel öğeleri ve değerlerini YerelLer **penceresinde** görüntüler.

 YERELleri görüntülemek için DE, EE'a ait [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemini çağırarak bir değerlendirme bağlamı (simge sağlayıcısı (SP), geçerli yürütme adresi ve bir bağlayıcı nesnesi verir. Daha fazla bilgi için [bkz. Değerlendirme bağlamı.](../../extensibility/debugger/evaluation-context.md) Çağrı başarılı olursa yöntem, geçerli yürütme adresini içeren yöntemi temsil eden bir `IDebugExpressionEvaluator::GetMethodProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

 DE, yalnızca yerel değerlerin dönüşecek şekilde filtrelenmiş ve yerel yapıların listesini üretmek için numaralandırarak [bir IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi almak için [EnumChildren'DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağırıyor. [](../../extensibility/debugger/reference/debug-property-info.md) Her yapı bir yerelin adını, türünü ve değerini içerir. Tür ve değer biçimlendirilmiş dizeler olarak depolanır ve görüntülenmeye uygundur. Ad, tür ve değer genellikle YerelLer penceresinin bir **satırda birlikte** görüntülenir.

> [!NOTE]
> QuickWatch ve **Watch pencereleri** aynı ad, değer ve tür biçimine sahip değişkenleri de görüntüler.  Ancak, bu değerler yerine [GetPropertyInfo çağrılarak](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) elde `IDebugProperty2::EnumChildren` edilir.

## <a name="in-this-section"></a>Bu bölümde
 [Yerellerin örnek uygulaması](../../extensibility/debugger/sample-implementation-of-locals.md) Örnekleri, yerelleri uygulama sürecinde adım adım kullanır.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) Hata ayıklama altyapısı (DE) ifade değerlendiriciyi (EE) çağırsa, üç bağımsız değişken geçer.

## <a name="see-also"></a>Ayrıca bkz.
 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
