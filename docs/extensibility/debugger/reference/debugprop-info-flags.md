---
title: DEBUGPROP_INFO_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737398"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Hata ayıklama özelliği nesnesi hakkında hangi bilgilerin alıncaya kadar alınacağa ilişkindir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`DEBUGPROP_INFO_FULLNAME`\
`bstrFullName` Alanı başlatma/kullanma.

`DEBUGPROP_INFO_NAME`\
`bstrName` Alanı başlatma/kullanma.

`DEBUGPROP_INFO_TYPE`\
`bstrType` Alanı başlatma/kullanma.

`DEBUGPROP_INFO_VALUE`\
`bstrValue` Alanı başlatma/kullanma.

`DEBUGPROP_INFO_ATTRIB`\
`dwAttrib` Alanı başlatma/kullanma.

`DEBUGPROP_INFO_PROP`\
`pProperty` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi içeren alanı başlatma/kullanma.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Değer alanının, varsa bu tür bir nesne için otomatik olarak genişletilmiş değeri içermesi gerektiğini belirtir.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Kullanım dışı.

`DEBUGPROP_INFO_VALUE_RAW`\
Güzelleştirilmiş değerleri veya üyeleri döndürmeyin (diğer bir şekilde değerleri biçimlendirmeyin).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Sentezlenmiş özel değerler döndürmeyin (örneğin, bir `ToString()` değer üretmek için bir nesneyi çağırmayın).

`DEBUGPROP_INFO_NONE`\
Bayrak ların ayarlatılolmadığını belirtir.

`DEBUGPROP_INFO_STANDARD`\
Initialize/use `dwAttrib`, `bstrName` `bstrType`, `bstrValue` ve alanları.

`DEBUGPROP_INFO_All`\
Tüm bayrakların maskesini gösterir.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısının hangi alanların başharfe geçirileceğini belirtmek için [GetPropertyInfo,](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)ve [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) yöntemlerine aktarılır.

Bu değerler, `dwFields` `DEBUG_PROPERTY_INFO` yapının hangi alanlarının kullanıldığını belirtmek için yapının üyesi için de kullanılır ve yapı döndürüldüğünde geçerlidir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
