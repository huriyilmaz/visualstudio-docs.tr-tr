---
title: Yerlilerin Örnek Uygulaması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713080"
---
# <a name="sample-implementation-of-locals"></a>Yerel halktan örnek uygulama
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Aşağıda Visual Studio ifade değerlendiricisi (EE) bir yöntem için yerel alır nasıl bir bakış:

1. Visual Studio hata ayıklama motorunun (DE) [GetDebugProperty'ini,](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) yerel halk da dahil olmak üzere yığın çerçevesinin tüm özelliklerini temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi almak için çağırır.

2. `IDebugStackFrame2::GetDebugProperty`kesme noktasının bulunduğu yöntemi açıklayan bir nesne almak için [GetMethodProperty'i](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) çağırır. DE bir sembol sağlayıcısı[(IDebugSymbolProvider),](../../extensibility/debugger/reference/idebugsymbolprovider.md)bir adres[(IDebugAddress)](../../extensibility/debugger/reference/idebugaddress.md)ve bağlayıcı[(IDebugBinder)](../../extensibility/debugger/reference/idebugbinder.md)sağlar.

3. `IDebugExpressionEvaluator::GetMethodProperty`belirtilen adresi içeren yöntemi `IDebugAddress` temsil eden bir [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) almak için verilen nesne ile [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) çağırır.

4. Arabirim `IDebugContainerField` [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimi için sorgulanır. Yöntemin yerel halka erişimini sağlayan bu arayüz.

5. `IDebugExpressionEvaluator::GetMethodProperty`yöntemin `IDebugProperty2` yerel lerini temsil `CFieldProperty` etmek için arabirimi çalıştıran bir sınıfı (örnekte adlandırılır) anında yönlendirir. Nesne `IDebugMethodField` `CFieldProperty` , `IDebugSymbolProvider`, `IDebugAddress`ve `IDebugBinder` nesneler ile birlikte bu nesneye yerleştirilir.

6. Nesne baş harfe getized olduğunda, `IDebugMethodField` [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntem kendisi hakkında tüm görüntülenebilir bilgileri içeren bir FIELD_INFO yapısı almak için nesne üzerinde çağrılır. [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) `CFieldProperty`

7. `IDebugExpressionEvaluator::GetMethodProperty`nesneyi `CFieldProperty` nesne `IDebugProperty2` olarak döndürür.

8. Visual Studio, metnin yerel `IDebugProperty2` öğelerini `guidFilterLocalsPlusArgs`içeren bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesini döndüren filtreyle döndürülen nesneüzerinde [EnumChildren'ı](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağırır. Bu [numaralandırma, EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) ve [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)çağrıları ile doldurulur.

9. Visual Studio, her yerel için [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) bir yapı elde etmek için [Next'i](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) arar. Bu yapı, yerel `IDebugProperty2` bir arabirim için bir işaretçi içerir.

10. Visual Studio, yerel in adını, değerini ve türünü elde etmek için her yerel için [GetPropertyInfo'yu](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) çağırır. Bu bilgiler **Yereller** penceresinde görüntülenir.

## <a name="in-this-section"></a>Bu bölümde
 [GetMethodProperty uygula](../../extensibility/debugger/implementing-getmethodproperty.md) [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)uygulamasını açıklar.

 [Yerel leri sayısal](../../extensibility/debugger/enumerating-locals.md) Hata ayıklama altyapısının (DE) yerel değişkenleri veya bağımsız değişkenleri ayıklamak için nasıl bir çağrı yaptığını açıklar.

 [Yerel özellikleri alın](../../extensibility/debugger/getting-local-properties.md) DE'nin bir veya daha fazla yerel kişinin adını, türünü ve değerini almak için nasıl arama yaptığını açıklar.

 [Yerel değerleri alın](../../extensibility/debugger/getting-local-values.md) Değerlendirme bağlamında verilen bağlayıcı nesnenin hizmetlerini gerektiren yerel in değerini alma tartışır.

 [Yerel leri değerlendirin](../../extensibility/debugger/evaluating-locals.md) Yerel halk nasıl değerlendirilir açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md) DE ifade değerlendiricisi (EE) çağırdığında geçirilen bağımsız değişkenleri sağlar.

 [MyCEE örneği](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) MyC dili için bir ifade değerlendiricisi oluşturmak için bir uygulama yaklaşımı gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel halkların görüntülenmesi](../../extensibility/debugger/displaying-locals.md)
