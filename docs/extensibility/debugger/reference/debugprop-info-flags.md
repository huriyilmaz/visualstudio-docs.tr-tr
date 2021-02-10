---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 745ecf4efa661c31e230a25d23cfd66cb5d5bb51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939129"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Bir hata ayıklama özelliği nesnesi hakkında hangi bilgilerin alınması gerektiğini belirtir.

## <a name="syntax"></a>Syntax

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
Alanı başlatın/kullanın `bstrFullName` .

`DEBUGPROP_INFO_NAME`\
Alanı başlatın/kullanın `bstrName` .

`DEBUGPROP_INFO_TYPE`\
Alanı başlatın/kullanın `bstrType` .

`DEBUGPROP_INFO_VALUE`\
Alanı başlatın/kullanın `bstrValue` .

`DEBUGPROP_INFO_ATTRIB`\
Alanı başlatın/kullanın `dwAttrib` .

`DEBUGPROP_INFO_PROP`\
`pProperty` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi içeren alanı başlatın/kullanın.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Değer alanının, varsa, bu nesne türü için otomatik genişletilmiş değeri içermesi gerektiğini belirtir.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Kullanım dışı.

`DEBUGPROP_INFO_VALUE_RAW`\
Herhangi bir beautified değeri veya üye döndürmeyin (yani, değerleri biçimlendirmeyin).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Özel bir sentezlenmiş değer döndürmez (örneğin, `ToString()` bir değer üretmek için bir nesne üzerinde çağırmayın).

`DEBUGPROP_INFO_NONE`\
Hiçbir bayrak ayarlanolmadığını belirtir.

`DEBUGPROP_INFO_STANDARD`\
`dwAttrib`,, `bstrName` `bstrType` Ve alanlarını başlatın/kullanın `bstrValue` .

`DEBUGPROP_INFO_All`\
Tüm bayrakların maskesini belirtir.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısını hangi alanların başlattığını göstermek Için [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)ve [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) yöntemlerine geçirilir.

Bu değerler, yapının üyesi için yapının `dwFields` `DEBUG_PROPERTY_INFO` hangi alanların kullanıldığını ve yapı döndürüldüğünde geçerli olduğunu göstermek için de kullanılır.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
