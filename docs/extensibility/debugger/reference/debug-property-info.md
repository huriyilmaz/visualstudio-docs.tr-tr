---
title: DEBUG_PROPERTY_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737453"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Hata ayıklama özelliği hakkında bilgi içerir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Üyeler
`dwValidFields`\
[Hangi](../../../extensibility/debugger/reference/debugprop-info-flags.md) alanların doldurulduğuna DEBUGPROP_INFO_FLAGS numaralandırmadan gelen bayrakların birleşimi.

`bstrFullName`\
Mülkün tam adı.

`bstrName`\
Bir bağlam içinde özellik adı.

`bstrType`\
Biçimlendirilmiş bir dize olarak özellik türü.

`bstrValue`\
Biçimlendirilmiş bir dize olarak özellik değeri.

`pProperty`\
Bu yapı tarafından açıklanan [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi.

`dwAttrib`\
Bu özelliğin özniteliklerini açıklayan [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) numaralandırma dan bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
Özellik, adı, türü ve değeri olan hiyerarşik bir niteliğe sahip bir nesnedir. Örneğin, bir özellik yerel değişkenleri, parametreleri, izleme değişkenlerini ve ifadeleri ve kayıtları açıklayabilir.

Bu yapı doldurulduğu [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemine geçirilir. Bu yapı aynı zamanda, sırayla, [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) ve [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) yöntemleri için bir çağrı döndürülür [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) arabiriminden bu yapının bir listesinin bir parçası olarak döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
