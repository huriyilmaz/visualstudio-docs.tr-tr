---
description: Bu arabirim bir yığın çerçevesi özelliğini, bir program belgesi özelliğini ya da başka bir özelliği temsil eder.
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42cdd3f9e5fd1d92e007bb9a15cf9e1fa5e44e83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171458"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Bu arabirim bir yığın çerçevesi özelliğini, bir program belgesi özelliğini ya da başka bir özelliği temsil eder. Özelliği genellikle bir ifade değerlendirmesinin sonucudur.

> [!NOTE]
> Bu "Property" kullanımı, bu `IDebugProperty2` tür bir varlığı temsil edebilir ancak bir sınıfın üye değişkeni anlamı olan ile karıştırılmamalıdır.

## <a name="syntax"></a>Syntax

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, belirli bir değer türünü temsil etmek için DE bu arabirimi uygular. Örneğin, değer bir ifade değerlendirmesinin sonucu olarak sayısal bir değer, bellek görüntülemek için kullanılan bir bellek bağlamı veya bir kayıt listesi ve bunların değerleri olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir değerlendirmenin sonucunu temsil eden bu arabirimi edinmek için [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) çağırın. `IDebugExpression2::EvaluateAsync` Bu arabirimi, SDM 'ye bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi göndererek döndürür, bu da özelliği almak Için [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) öğesini çağırır.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) , ilişkili betik belgesini sağlamak için bu arabirimi döndürür.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) , bir işlevin dönüş değerini temsil etmek için bu arabirimi döndürür.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) , programın bir ad veya bellek bağlamı gibi çeşitli özelliklerini temsil etmek için bu arabirimi döndürür.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) bu arabirimi, yerel değişkenler gibi yığın çerçevesinin çeşitli özelliklerini temsil edecek şekilde döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProperty2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Bir özelliği açıklayan [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısını doldurur.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Bir dizeden bir özelliğin değerini ayarlar.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Özelliğin değerini belirli bir başvurunun değerinden ayarlar.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Bir özelliğin alt öğelerini numaralandırır.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Bir özelliğin üst öğesini döndürür.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Bir özelliğin en çok türetilmiş özelliğini açıklayan özelliği döndürür.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Bir özelliğin değerini oluşturan bellek baytlarını döndürür.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Bir özellik değeri için bellek bağlamını döndürür.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Özellik değerinin bayt cinsinden boyutunu döndürür.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Bu özelliğin değerine bir başvuru döndürür.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Bir özelliğin genişletilmiş bilgilerini döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bir arabirim tarafından temsil edilen bir özellik, bir `IDebugProperty2` ada, türe ve adrese sahip bir değer olarak düşünülebilir. Daha genel koşullarda, `IDebugProperty2` üst ve alt düğümleri ile hiyerarşik bir yapıya sahip herhangi bir şeyi temsil edebilir.

 Genellikle bir özellik, yalnızca geçerli yığın çerçevesi olarak, örneğin, yalnızca geçerli yığın çerçevesinin olduğu sürece geçici olarak yapılır. Diğer taraftan, [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi tarafından temsil edilen bir başvuru, değer bellekte kaldığı sürece sürer.

 IDE, `IDebugProperty2` kullanıcıların çalışma zamanında özelliklere gözatmasını ve bunları değiştirmesini sağlamak için arabirimini kullanabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
