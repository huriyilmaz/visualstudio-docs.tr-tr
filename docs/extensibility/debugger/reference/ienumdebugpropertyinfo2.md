---
title: IEnumDebugEmlakInfo2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715348"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Bu arabirim [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapıları sayısallandırır.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), belirli bir özelliğin bilgilerini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Belirli bir özelliğin çocuklarını temsil eden bu arabirimi elde etmek için [EnumChildren'ı](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) arayın. Belirli bir yığın çerçevesinin özelliklerini temsil eden bu arabirimi elde etmek için [EnumProperties'i](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugPropertyInfo2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Numaralandırma sırasında belirli sayıda [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapı alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Numaralandırma sırasında belirli sayıda [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapıyı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Bir numaralandırmadaki [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapıların sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Genel olarak, özellik, bir ad, değer, adres ve tür yanı sıra ilişkili özellik nesnesi veya yığın çerçevesine uygun diğer bilgileri içerebilir bilgi hiyerarşisi. Daha fazla bilgi için [IDebugProperty2'ye](../../../extensibility/debugger/reference/idebugproperty2.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
