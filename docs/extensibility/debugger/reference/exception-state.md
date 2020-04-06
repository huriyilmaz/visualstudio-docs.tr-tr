---
title: EXCEPTION_STATE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736962"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Özel durum durumunu belirtir.

## <a name="syntax"></a>Sözdizimi

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
İstisnadan durmayın.

`EXCEPTION_STOP_FIRST_CHANCE`\
İstisnanın ilk ateşini ilk durdurun. Bir özel durum olayı açıklanırken, bu bayrak özel durum olayının ilk şans özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_SECOND_CHANCE`\
İstisnanın ikinci atışında durun. Bir özel durum olayı açıklanırken, özel durum olayının ikinci şans özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Bir kullanıcı modu özel durum ilk ateş durdurun. Bir özel durum olayını açıklarken, özel durum olayının ilk şans kullanıcı özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Kullanıcı modu özel durum yakalanmadığında durdurun. Bir özel durum olayını açıklarken, özel durum olayının yakalanmamış bir kullanıcı modu özel durum olayı olduğunu gösterir.

`EXCEPTION_STOP_ALL`\
Herhangi bir istisna dışında dur. Özel durum olayını açıklarken kullanılmaz.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Bir özel durum olayı açıklandığında, özel durum devam edilemez gösterir.

`EXCEPTION_CODE_SUPPORTED`\
Özel durum destekleyen kod olduğunu gösterir. Özel durum görüntülemede kullanılır

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Özel durum kodunun hexadecimal olarak görüntülenmesi gerektiğini gösterir. Özel durum görüntülemede kullanılır.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Özel durum kodunun JustMyCode'u desteklediğini gösterir. Özel durum görüntülemede kullanılır.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Yönetilen kod hata ayıklayıcısının özel durumları işlemesi gerektiğini gösterir. Ayaredilmezse, varsayılan hata ayıklama özel durumları işler. Bu [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemine geçirilir ve [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısında kullanılmaz.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
ESKI, KULLANMAYıN.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
ESKI, KULLANMAYıN.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
ESKI, KULLANMAYıN.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
ESKI, KULLANMAYıN.

## <a name="remarks"></a>Açıklamalar
`dwState` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısının üyesi olarak özel durum durumunu ve bu konuda neler yapılabileceğini belirtmek için kullanılır.

Bu değerler, tüm özel durumların durumunu ayarlamak için [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemine de geçirilir.

Bu bayraklar biraz veya biraz veya birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
