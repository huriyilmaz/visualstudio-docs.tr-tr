---
description: Özel durum durumunu belirtir.
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33c7f939a8f630592890c3c03be662099680e64b87d4179425497ee864a6718c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262522"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Özel durum durumunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Alanlar
`EXCEPTION_NONE`\
Özel durum için durmayın.

`EXCEPTION_STOP_FIRST_CHANCE`\
Özel durumun ilk at at at durdurun. Bir özel durum olayı açıkken, bu bayrak özel durum olayı bir ilk şans özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_SECOND_CHANCE`\
Özel durumun saniyelik olarak at at at. Bir özel durum olayı açıkken, özel durum olayı ikinci şans özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Kullanıcı modu özel durumu ilk başta kesildi. Bir özel durum olayı açıkken, özel durum olayı bir ilk şans kullanıcı özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Kullanıcı modu özel durumu yakalanmazken durdurun. Bir özel durum olayı açıkken, özel durum olayı yakalanmayan bir kullanıcı modu özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_ALL`\
Herhangi bir özel durumda durdurun. Özel durum olayı açıklanmaz.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Bir özel durum olayı açıklandıken, özel durumun devam edelenemleri olduğunu gösterir.

`EXCEPTION_CODE_SUPPORTED`\
Özel durumun destekleyen kodu olduğunu gösterir. Özel durum görüntülenirken kullanılır

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Özel durum kodunun onaltılık olarak görüntülendiğinden belirtir. Özel durum görüntülemede kullanılır.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Özel durum kodunun JustMyCode'i desteklediğini gösterir. Özel durum görüntülemede kullanılır.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Yönetilen kod hata ayıklayıcısının özel durumları işlemesi gerektiğini gösterir. Ayarlanmazsa, varsayılan hata ayıklayıcısı özel durumları işler. Bu, [SetAllExceptions yöntemine](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) geçirildi ve [](../../../extensibility/debugger/reference/exception-info.md) EXCEPTION_INFO kullanılmadı.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
KULLANıMDAN KALDıRıLMıŞ, KULLANMA.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
KULLANıMDAN KALDıRıLMıŞ, KULLANMA.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
KULLANıMDAN KALDıRıLMıŞ, KULLANMA.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
KULLANıMDAN KALDıRıLMıŞ, KULLANMA.

## <a name="remarks"></a>Açıklamalar
Özel durumun durumunu ve bu EXCEPTION_INFO ne yaplrı olduğunu belirtmek için genel `dwState` yönetim yapısının üyesi olarak kullanılır. [](../../../extensibility/debugger/reference/exception-info.md)

Bu değerler tüm özel durumların [durumunu ayarlamak için SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemine de geçirildi.

Bu bayraklar bitwise OR ile birleştirilmiş olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
