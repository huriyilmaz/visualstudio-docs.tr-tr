---
description: Alan türü için değiştiriciler belirtir.
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e74dec064f2603fa19745ec0abab8b7a402307a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119977"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Alan türü için değiştiriciler belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_MODIFIERS {
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
Alana erişilemediğini belirtir.

`FIELD_MOD_ACCESS_PUBLIC`\
Alanın genel erişimi olduğunu gösterir.

`FIELD_MOD_ACCESS_PROTECTED`\
Alanın korumalı erişimi olduğunu gösterir.

`FIELD_MOD_ACCESS_PRIVATE`\
Alanın özel erişimi olduğunu gösterir.

`FIELD_MOD_NOMODIFIERS`\
Alanda değiştiriciler olmadığını gösterir.

`FIELD_MOD_STATIC`\
Alanın statik olduğunu gösterir.

`FIELD_MOD_CONSTANT`\
Alanın bir sabit olduğunu gösterir.

`FIELD_MOD_TRANSIENT`\
Alanın geçici olduğunu gösterir.

`FIELD_MOD_VOLATILE`\
Alanın geçici olduğunu gösterir.

`FIELD_MOD_ABSTRACT`\
Alanın soyut olduğunu gösterir.

`FIELD_MOD_NATIVE`\
Alanın yerel olduğunu gösterir.

`FIELD_MOD_SYNCHRONIZED`\
Alanın eşitleneceğini belirtir.

`FIELD_MOD_VIRTUAL`\
Alanın sanal olduğunu gösterir.

`FIELD_MOD_INTERFACE`\
Alanın bir arabirim olduğunu gösterir.

`FIELD_MOD_FINAL`\
Alanın son olduğunu gösterir.

`FIELD_MOD_SENTINEL`\
Alanın Sentinel olduğunu gösterir.

`FIELD_MOD_INNERCLASS`\
Alanın bir iç sınıf olduğunu gösterir.

`FIELD_TYPE_OPTIONAL`\
Alanın isteğe bağlı olduğunu gösterir.

`FIELD_MOD_BYREF`\
Alanın bir başvuru bağımsız değişkeni olduğunu gösterir. Bu özel olarak Yöntem bağımsız değişkenleri içindir.

`FIELD_MOD_HIDDEN`\
Alanın gizlenmesi gerektiğini veya başka bir bağlamda sunulmasını belirtir; Örneğin, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statik Yereller.

`FIELD_MOD_MARSHALASOBJECT`\
Alanın arabirime sahip bir nesneyi temsil ettiğini belirtir `IUnknown` .

`FIELD_MOD_SPECIAL_NAME`\
Alanın `.ctor` bir Oluşturucu (yalnızca) için özel bir ada sahip olduğunu gösterir [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

`FIELD_MOD_HIDEBYSIG`\
Alanın `Overloads` kendisine uygulanmış anahtar sözcüğü olduğunu belirtir ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] yalnızca).

`FIELD_MOD_WRITEONLY`\
Alanın salt yazılır olduğunu gösterir. Yalnızca bu `FIELD_MOD_ALL` tür salt yazılır alanların kullanımı işlev değerlendirmesi için olduğundan, bu değer öğesine dahil değildir. Kullanıcının alanları açıkça istemesi gerekir `FIELD_MOD_WRITEONLY` .

`FIELD_MOD_ACCESS_MASK`\
Alan erişimi için bir maske gösterir.

`FIELD_MOD_MASK`\
Alan değiştiricileri için bir maske gösterir.

## <a name="remarks"></a>Açıklamalar
`dwModifiers` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısının üyesi için kullanılır.

Bu değerler, belirli alanları filtrelemek için [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) yöntemine de geçirilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
