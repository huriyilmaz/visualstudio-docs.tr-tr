---
title: Yereller için örnek uygulama | Microsoft Docs
description: Visual Studio, bu makaledeki ifade değerlendiricisi ' nden bir yöntemin yerelleri nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 71b358543463e8c780a122dfa466651639f5a906
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063635"
---
# <a name="sample-implementation-of-locals"></a>Yereller için örnek uygulama
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 aşağıda, Visual Studio ifade değerlendiricisi (EE) ' dan bir yöntemin yerelleri nasıl aldığından ilgili bir genel bakış verilmiştir:

1. Visual Studio, yereller de dahil olmak üzere yığın çerçevesinin tüm özelliklerini temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi almak için hata ayıklama altyapısının (DE) [getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) öğesini çağırır.

2. `IDebugStackFrame2::GetDebugProperty` kesme noktasının gerçekleştiği yöntemi açıklayan bir nesne almak için [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) ' i çağırır. DE bir sembol sağlayıcısı ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), bir adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) ve bir Ciltçi ([ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md)) sağlar.

3. `IDebugExpressionEvaluator::GetMethodProperty`[](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) `IDebugAddress` belirtilen adresi içeren yöntemi temsil eden bir [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) almak Için sağlanan nesneyle GetContainerField öğesini çağırır.

4. `IDebugContainerField`Arabirim, [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimi için sorgulanır. Yöntemin Yereller için erişim sağlayan bu arabirimdir.

5. `IDebugExpressionEvaluator::GetMethodProperty``CFieldProperty` `IDebugProperty2` yöntemin yerelleri temsil etmek için arabirimi çalıştıran bir sınıfı (örnekte çağırılır) başlatır. `IDebugMethodField`Nesnesi `CFieldProperty` ,, `IDebugSymbolProvider` `IDebugAddress` ve nesneleriyle birlikte bu nesneye yerleştirilir `IDebugBinder` .

6. `CFieldProperty`Nesne başlatıldığında, [](../../extensibility/debugger/reference/idebugfield-getinfo.md) `IDebugMethodField` yöntemin kendisi hakkında görüntülenebilen tüm bilgileri içeren [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) yapısını almak için nesnesi üzerinde GetInfo çağırılır.

7. `IDebugExpressionEvaluator::GetMethodProperty` nesneyi `CFieldProperty` nesne olarak döndürür `IDebugProperty2` .

8. Visual Studio, [](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) döndürülen `IDebugProperty2` nesnede `guidFilterLocalsPlusArgs` , metodun yerellerini içeren bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndüren, filtre ile enumchildren 'ı çağırır. Bu numaralandırma, [Enumyereller](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) ve [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)çağrıları tarafından doldurulur.

9. Visual Studio her bir yerel için [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapısını elde etmek [için çağırır.](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) Bu yapı yerel için bir arabirime yönelik bir işaretçi içerir `IDebugProperty2` .

10. Visual Studio, yerel sunucunun adını, değerini ve türünü almak için her bir yerel için [getpropertyınfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) çağırır. Bu bilgiler **Yerel öğeler** penceresinde görüntülenir.

## <a name="in-this-section"></a>Bu bölümde
 [GetMethodProperty Uygula](../../extensibility/debugger/implementing-getmethodproperty.md) [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)uygulamasının bir uygulamasını açıklar.

 [Yerelleri listeleme](../../extensibility/debugger/enumerating-locals.md) Hata ayıklama altyapısının (DE) yerel değişkenleri veya bağımsız değişkenleri numaralandırmak için nasıl çağrı yapıldığını açıklar.

 [Yerel özellikleri al](../../extensibility/debugger/getting-local-properties.md) ' Nin, bir veya daha fazla yerelin adını, türünü ve değerini almak için nasıl bir çağrı yaptığı açıklanmıştır.

 [Yerel değerleri Al](../../extensibility/debugger/getting-local-values.md) Değerlendirme bağlamı tarafından verilen bir Ciltçi nesnesinin hizmetlerini gerektiren yerel öğesinin değerini almayı açıklar.

 [Yerelleri değerlendir](../../extensibility/debugger/evaluating-locals.md) Yereller nasıl değerlendirildiğini açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) , İfade değerlendirici (EE) çağırdığında geçirilen bağımsız değişkenleri sağlar.

 [MyCEE örneği](/previous-versions/) MyC dili için bir ifade değerlendiricisi oluşturmaya yönelik bir uygulama yaklaşımını gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)