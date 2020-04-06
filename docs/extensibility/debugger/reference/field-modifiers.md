---
title: FIELD_MODIFIERS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736848"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Bir alan türü için değiştiriciler belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Alanlar
`FIELD_MOD_ACCESS_TYPE`\
Alana erişilemediğini gösterir.

`FIELD_MOD_ACCESS_PUBLIC`\
Alanın genel erişime sahip olduğunu gösterir.

`FIELD_MOD_ACCESS_PROTECTED`\
Alanın erişimi koruduğunu gösterir.

`FIELD_MOD_ACCESS_PRIVATE`\
Alanın özel erişimi olduğunu gösterir.

`FIELD_MOD_NOMODIFIERS`\
Alanın değiştirici olmadığını gösterir.

`FIELD_MOD_STATIC`\
Alanın statik olduğunu gösterir.

`FIELD_MOD_CONSTANT`\
Alanın sabit olduğunu gösterir.

`FIELD_MOD_TRANSIENT`\
Alanın geçici olduğunu gösterir.

`FIELD_MOD_VOLATILE`\
Alanın değişken olduğunu gösterir.

`FIELD_MOD_ABSTRACT`\
Alanın soyut olduğunu gösterir.

`FIELD_MOD_NATIVE`\
Alanın yerel olduğunu gösterir.

`FIELD_MOD_SYNCHRONIZED`\
Alanın eşitolduğunu gösterir.

`FIELD_MOD_VIRTUAL`\
Alanın sanal olduğunu gösterir.

`FIELD_MOD_INTERFACE`\
Alanın bir arabirim olduğunu gösterir.

`FIELD_MOD_FINAL`\
Alanın son olduğunu gösterir.

`FIELD_MOD_SENTINEL`\
Alanın bir sentinel olduğunu gösterir.

`FIELD_MOD_INNERCLASS`\
Alanın bir iç sınıf olduğunu gösterir.

`FIELD_TYPE_OPTIONAL`\
Alanın isteğe bağlı olduğunu gösterir.

`FIELD_MOD_BYREF`\
Alanın bir başvuru bağımsız değişkeni olduğunu gösterir. Bu özellikle yöntem bağımsız değişkenleri içindir.

`FIELD_MOD_HIDDEN`\
Alanın gizlenmesi veya başka bir bağlamda sunulması gerektiğini gösterir; örneğin, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statik yerel.

`FIELD_MOD_MARSHALASOBJECT`\
Alanın `IUnknown` arabirimi olan bir nesneyi temsil ettiğini gösterir.

`FIELD_MOD_SPECIAL_NAME`\
Alanın özel bir adı olduğunu gösterir, `.ctor` örneğin, bir[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] oluşturucu için (yalnızca).

`FIELD_MOD_HIDEBYSIG`\
Alanın anahtar kelimesinin `Overloads` ona uygulandığını[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] gösterir (yalnızca).

`FIELD_MOD_WRITEONLY`\
Alanın yalnızca yazma olduğunu gösterir. Bu `FIELD_MOD_ALL`değer, yalnızca yazma alanlarının tek kullanımı işlev değerlendirmesi için olduğundan, bu değere dahil edilmez. Bir kullanıcı açıkça `FIELD_MOD_WRITEONLY` alanları istemelidir.

`FIELD_MOD_ACCESS_MASK`\
Alan erişimi için bir maskegösterir.

`FIELD_MOD_MASK`\
Alan değiştiriciler için bir maske gösterir.

## <a name="remarks"></a>Açıklamalar
`dwModifiers` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısının üyesi için kullanılır.

Bu değerler, belirli alanlar için filtrelemek için [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) yöntemine de aktarılır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
