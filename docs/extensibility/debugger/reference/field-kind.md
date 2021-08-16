---
description: Bir IDebugField nesnesinde bulunan alan türünü belirtir.
title: FIELD_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cfeba85222748642edf2125db51aff6812bd8e4874aaacc5ccde6bbce86b3b21
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403227"
---
# <a name="field_kind"></a>FIELD_KIND
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinde bulunan alan türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_KIND {
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
    FIELD_SYM_MEMBER      = 0x01000000,
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
    FIELD_SYM_MEMBER      = 0x01000000,
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
Alanın, tür, ad ve diğer bilgilerle bir sembol olduğunu gösterir.

`FIELD_TYPE_PRIMITIVE`\
Alanın temel bir veri türü olduğunu gösterir.

`FIELD_TYPE_STRUCT`\
Alanın bir yapı olduğunu gösterir.

`FIELD_TYPE_CLASS`\
Alanın bir sınıf olduğunu belirtir.

`FIELD_TYPE_INTERFACE`\
Alanın bir arabirim olduğunu gösterir.

`FIELD_TYPE_UNION`\
Alanın bir Union olduğunu gösterir.

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
Alanın bir bitfield olduğunu gösterir.

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
Alanın "This" işaretçisi olduğunu gösterir.

`FIELD_SYM_GLOBAL`\
Alanın genel olduğunu gösterir.

`FIELD_SYM_PROP_GETTER`\
Alanın özellikleri alacağını belirtir.

`FIELD_SYM_PROP_SETTER`\
Alanın özellikleri ayarladığını gösterir.

`FIELD_SYM_EXTENDED`\
Daha sonraki kullanımlar için ayrılmıştır.

`FIELD_KIND_MASK`\
Alan türleri için bir maske gösterir.

`FIELD_TYPE_MASK`\
Alan türleri için bir maske gösterir.

`FIELD_SYM_MASK`\
Sembol bilgileri için bir maske gösterir.

## <a name="remarks"></a>Açıklamalar
[Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) metoduna yapılan çağrıdan döndürülür.

Alan türüne bağlı olarak, [QueryInterface](/cpp/atl/queryinterface) daha belirli bir arabirim formu Için [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminde çağrılabilir. Örneğin, [Getkinleştirme d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürülürse `FIELD_TYPE_METHOD` , `QueryInterface` `DebugField` [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) arabirimini elde etmek için i 'yi çağırabilirsiniz.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
