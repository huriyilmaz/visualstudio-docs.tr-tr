---
title: IDebugÖzellik2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721229"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Bu arabirim, yığın çerçevesi özelliğini, program belge özelliğini veya başka bir özelliği temsil eder. Özellik genellikle bir ifade değerlendirme sonucudur.

> [!NOTE]
> "Özellik" bu kullanımı bir sınıfın bir üye değişken anlamı ile `IDebugProperty2` karıştırılmamalıdır, ancak bir tür bir varlık temsil edebilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, belirli bir değer türünü temsil etmek için bu arabirimi uygular. Örneğin, bir ifade değerlendirmesi, bellek görüntülemek için kullanılan bir bellek bağlamı veya kayıt listesi ve değerleri sonucunda değer sayısal bir değer olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir değerlendirmenin sonucunu temsil eden bu arabirimi elde etmek için [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync'i](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) arayın. `IDebugExpression2::EvaluateAsync`Bu arabirimi, sdm'ye bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi göndererek döndürür ve bu arabirimi özelliği almak için [GetResult'ı](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) arar.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) ilişkili komut dosyası belgesini sağlamak için bu arabirimi döndürür.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) bu arabirimi bir işlevin geri dönüş değerini temsil etmek için döndürür.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) bu arabirimi, bir ad veya bellek bağlamı gibi programın çeşitli özelliklerini temsil edecek şekilde döndürür.

- [GetDebugProperty,](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) bu arabirimi yerel değişkenler gibi yığın çerçevesinin çeşitli özelliklerini temsil edecek şekilde döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProperty2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Bir özelliği açıklayan [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) bir yapıyı doldurur.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Bir özelliğin değerini bir dizeden ayarlar.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Belirli bir referansın değerinden özelliğin değerini ayarlar.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Bir mülkün çocuklarını taklit eder.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Bir özelliğin üst öğesini döndürür.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Bir özelliğin en türetilmiş özelliğini açıklayan özelliği döndürür.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Bir özelliğin değerini oluşturan bellek baytlarını döndürür.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Özellik değeri için bellek bağlamını döndürür.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Özellik değerinin boyutunu baytolarak verir.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Bu özelliğin değerine bir başvuru verir.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Bir özelliğin genişletilmiş bilgilerini verir.|

## <a name="remarks"></a>Açıklamalar
 Bir `IDebugProperty2` arabirim tarafından temsil edilen bir özellik, bir ad, tür ve adres içeren bir değer olarak düşünülebilir. Daha genel anlamda, `IDebugProperty2` bir hiyerarşik yapıya sahip bir şey temsil edebilir, ebeveynler ve alt düğümleri ile.

 Bir özellik genellikle geçicidir, yalnızca geçerli yığın çerçevesi kadar uzun sürer, örneğin. Diğer taraftan, bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi tarafından temsil edilen bir başvuru, değer bellekte kaldığı sürece devam eder.

 `IDebugProperty2` IDE, kullanıcıların çalışma zamanında mülklere göz atmasına ve bunları değiştirmesine izin vermek için arabirimi kullanabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
