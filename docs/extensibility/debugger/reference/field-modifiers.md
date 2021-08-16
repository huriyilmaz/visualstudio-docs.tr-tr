---
description: Bir alan türü için değiştiricileri belirtir.
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
ms.openlocfilehash: fa7d151e349d67a9a7edb781bdbf07c9b8523d03cd7b974b8b5a6f3c968c87d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403214"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Bir alan türü için değiştiricileri belirtir.

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
Alana erişilemediklerini gösterir.

`FIELD_MOD_ACCESS_PUBLIC`\
Alanın genel erişime sahip olduğunu gösterir.

`FIELD_MOD_ACCESS_PROTECTED`\
Alanın korumalı erişimi olduğunu gösterir.

`FIELD_MOD_ACCESS_PRIVATE`\
Alanın özel erişimi olduğunu gösterir.

`FIELD_MOD_NOMODIFIERS`\
Alanın değiştiricisi olmadığını gösterir.

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
Alanın eşitlenmiş olduğunu gösterir.

`FIELD_MOD_VIRTUAL`\
Alanın sanal olduğunu gösterir.

`FIELD_MOD_INTERFACE`\
Alanın bir arabirim olduğunu gösterir.

`FIELD_MOD_FINAL`\
Alanın son olduğunu gösterir.

`FIELD_MOD_SENTINEL`\
Alanın sentinel olduğunu gösterir.

`FIELD_MOD_INNERCLASS`\
Alanın bir iç sınıf olduğunu gösterir.

`FIELD_TYPE_OPTIONAL`\
Alanın isteğe bağlı olduğunu gösterir.

`FIELD_MOD_BYREF`\
Alanın bir başvuru bağımsız değişkeni olduğunu gösterir. Bu özellikle yöntem bağımsız değişkenleri içindir.

`FIELD_MOD_HIDDEN`\
Alanın gizli olması veya başka bir bağlamda sun olması gerektiğini gösterir; Örneğin, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statik yereller.

`FIELD_MOD_MARSHALASOBJECT`\
Alanın arabirimi olan bir nesneyi temsil ettiğini `IUnknown` gösterir.

`FIELD_MOD_SPECIAL_NAME`\
Alanın özel bir adı olduğunu gösterir; örneğin, `.ctor` bir oluşturucu için [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] (yalnızca).

`FIELD_MOD_HIDEBYSIG`\
Alanda anahtar sözcüğünün `Overloads` uygulandığını gösterir [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] (yalnızca).

`FIELD_MOD_WRITEONLY`\
Alanın yalnızca yazma olduğunu gösterir. Bu tür yalnızca yazma `FIELD_MOD_ALL` alanlarının tek kullanımı işlev değerlendirmesi için olduğu için bu değer içinde dahil değildir. Kullanıcının alanları açıkça istemesi `FIELD_MOD_WRITEONLY` gerekir.

`FIELD_MOD_ACCESS_MASK`\
Alan erişimi için bir maske gösterir.

`FIELD_MOD_MASK`\
Alan değiştiricileri için bir maske gösterir.

## <a name="remarks"></a>Açıklamalar
Bu `dwModifiers` yapının üyesi [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) kullanılır.

Bu değerler, belirli alanları filtrelemek [için EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) yöntemine de geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
