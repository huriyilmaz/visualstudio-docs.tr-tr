---
title: Yerel Halkların Görüntülenmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738937"
---
# <a name="display-locals"></a>Yerel leri görüntüleyin
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Yürütme her zaman içeren yöntem veya geçerli yöntem olarak da bilinen bir yöntem bağlamında gerçekleşir. Yürütme duraklatıldığında, Visual Studio hata ayıklama altyapısını (DE) yerel değişkenlerin ve bağımsız değişkenlerin listesini almak için çağırır ve bu da yöntemin yerel öğelerini topluca çağırır. Visual Studio bu yerlileri ve değerlerini **Yerel ler** penceresinde görüntüler.

 Yerel leri görüntülemek için DE, EE'ye ait [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemini çağırır ve ona bir değerlendirme bağlamı, yani bir sembol sağlayıcısı (SP), geçerli yürütme adresi ve bağlayıcı nesnesi verir. Daha fazla bilgi için [Değerlendirme bağlamına](../../extensibility/debugger/evaluation-context.md)bakın. Çağrı başarılı olursa, `IDebugExpressionEvaluator::GetMethodProperty` yöntem geçerli yürütme adresini içeren yöntemi temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

 DE, yalnızca yerel halkları döndürmek için filtre uygulanan ve [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapıların listesini oluşturmak için numaralandırılmış bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi almak için [EnumChildren'ı](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağırır. Her yapı, yerel bir yapının adını, türünü ve değerini içerir. Türü ve değeri, görüntü için uygun biçimlendirilmiş dizeleri olarak depolanır. Ad, tür ve değer genellikle **Yereller** penceresinin bir satırında birlikte görüntülenir.

> [!NOTE]
> **QuickWatch** ve **Watch** pencereleri de aynı ad, değer ve tür biçimine sahip değişkenleri görüntüler. Ancak, bu değerler [getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yerine `IDebugProperty2::EnumChildren`alınarak elde edilir.

## <a name="in-this-section"></a>Bu bölümde
 [Yerel halktan örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md) Yerel halk uygulama sürecinde adım için örnekler kullanır.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) Hata ayıklama altyapısı (DE) ifade değerlendiricisi (EE) aradığında, üç bağımsız değişkenden geçtiğini açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
