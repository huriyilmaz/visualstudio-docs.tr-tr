---
description: Hata ayıklama özelliği hakkında bilgi içerir.
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bd2526853dd5c0c3bb84bdc7d00c76805dd28a1118b4a35b8d173b17ab9bde3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452400"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Hata ayıklama özelliği hakkında bilgi içerir.

## <a name="syntax"></a>Syntax

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
Hangi alanların doldurulması [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) bayrağının bir birleşimi.

`bstrFullName`\
Özelliğin tam adı.

`bstrName`\
Bağlam içindeki özellik adı.

`bstrType`\
Özellik türü, biçimlendirilmiş bir dize olarak.

`bstrValue`\
Biçimlendirilmiş dize olarak özellik değeri.

`pProperty`\
Bu [yapı tarafından açıklanan IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi.

`dwAttrib`\
Bu özelliğin [özniteliklerini açıklayan DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) bayrağının bir birleşimi.

## <a name="remarks"></a>Açıklamalar
Özellik, adı, türü ve değeri olan hiyerarşik yapıya sahip bir nesnedir. Örneğin, bir özellik yerel değişkenleri, parametreleri, izleme değişkenlerini ve ifadelerini ve yazmalarını açıklar.

Bu yapı, [doldurulan GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemine geçirildi. Bu yapı ayrıca [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) arabiriminden bu yapı listesinin bir parçası olarak döndürülür ve bu da [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) ve [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) yöntemlerine yapılan bir çağrıdan döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
