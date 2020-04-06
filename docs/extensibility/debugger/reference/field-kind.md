---
title: FIELD_KIND | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cafe4a34745f3b34070f7d8fed1a246c806375a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736868"
---
# <a name="field_kind"></a>FIELD_KIND
[Bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinde bulunan alan türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`FIELD_KIND_TYPE`\
Alanın yalnızca bir tür olduğunu gösterir.

`FIELD_KIND_SYMBOL`\
Alanın türü, adı ve diğer bilgileri içeren bir sembol olduğunu gösterir.

`FIELD_TYPE_PRIMITIVE`\
Alanın ilkel bir veri türü olduğunu gösterir.

`FIELD_TYPE_STRUCT`\
Alanın bir yapı olduğunu gösterir.

`FIELD_TYPE_CLASS`\
Alanın bir sınıf olduğunu gösterir.

`FIELD_TYPE_INTERFACE`\
Alanın bir arabirim olduğunu gösterir.

`FIELD_TYPE_UNION`\
Alanın bir birlik olduğunu gösterir.

`FIELD_TYPE_ARRAY`\
Alanın bir dizi olduğunu gösterir.

`FIELD_TYPE_METHOD`\
Alanın bir yöntem olduğunu gösterir.

`FIELD_TYPE_BLOCK`\
Alanın bir blok olduğunu gösterir.

`FIELD_TYPE_POINTER`\
Alanın bir işaretçi olduğunu gösterir.

`FIELD_TYPE_ENUM`\
Alanın numaralandırılmış bir veri türü olduğunu gösterir.

`FIELD_TYPE_LABEL`\
Alanın bir etiket olduğunu gösterir.

`FIELD_TYPE_TYPEDEF`\
Alanın bir typedef olduğunu gösterir.

`FIELD_TYPE_BITFIELD`\
Alanın bir bit alanı olduğunu gösterir.

`FIELD_TYPE_NAMESPACE`\
Alanın bir ad alanı olduğunu gösterir.

`FIELD_TYPE_MODULE`\
Alanın bir modül olduğunu gösterir.

`FIELD_TYPE_DYNAMIC`\
Alanın dinamik olduğunu gösterir.

`FIELD_TYPE_PROP`\
Alanın bir özellik olduğunu gösterir.

`FIELD_TYPE_INNERCLASS`\
Alanın bir iç sınıf olduğunu gösterir.

`FIELD_TYPE_REFERENCE`\
Alanın bir başvuru olduğunu gösterir.

`FIELD_TYPE_EXTENDED`\
Daha sonraki kullanımlar için ayrılmıştır.

`FIELD_SYM_MEMBER`\
Alanın bir üye olduğunu gösterir.

`FIELD_SYM_LOCAL`\
Alanın yerel olduğunu gösterir.

`FIELD_SYM_PARAMETER`\
Alanın bir parametre olduğunu gösterir.

`FIELD_SYM_THIS`\
Alanın "bu" işaretçisi olduğunu gösterir.

`FIELD_SYM_GLOBAL`\
Alanın genel olduğunu gösterir.

`FIELD_SYM_PROP_GETTER`\
Alanın özellikleri aldığını gösterir.

`FIELD_SYM_PROP_SETTER`\
Alanın özellikleri ayarladığını gösterir.

`FIELD_SYM_EXTENDED`\
Daha sonraki kullanımlar için ayrılmıştır.

`FIELD_KIND_MASK`\
Alan türleri için bir maske gösterir.

`FIELD_TYPE_MASK`\
Alan türleri için bir maske gösterir.

`FIELD_SYM_MASK`\
Sembol bilgileri için bir maskeyi gösterir.

## <a name="remarks"></a>Açıklamalar
[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemine yapılan bir aramadan döndürülür.

Alanın türüne bağlı olarak, [QueryInterface](/cpp/atl/queryinterface) daha özel bir arabirim biçimi için [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminde çağrılabilir. Örneğin, [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) dönerse, `FIELD_TYPE_METHOD` `QueryInterface` [iDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) arabirimini almak için I'i`DebugField` arayabilirsiniz.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
