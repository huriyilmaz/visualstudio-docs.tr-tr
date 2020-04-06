---
title: DEBUGREF_INFO_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737382"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Hata ayıklama başvuru nesnesi hakkında hangi bilgilerin alıncaya kadar alınacağa değinin.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`DEBUGREF_INFO_NAME`\
Yapıdaki `bstrName` alanı başlatma/kullanma.

`DEBUGREF_INFO_TYPE`\
Yapıdaki `bstrType` alanı başlatma/kullanma.

`DEBUGREF_INFO_VALUE`\
Yapıdaki `bstrValue` alanı başlatma/kullanma.

`DEBUGREF_INFO_ATTRIB`\
Yapıdaki `dwAttrib` alanı başlatma/kullanma.

`DEBUGREF_INFO_REFTYPE`\
Yapıdaki `dwRefType` alanı başlatma/kullanma.

`DEBUGREF_INFO_REF`\
Yapıdaki `pReference` alanı başlatma/kullanma.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Değer alanı, varsa, bu tür bir nesne için otomatik olarak genişletilmiş değeri içermelidir.

`DEBUGREF_INFO_NONE`\
Bayrak ların ayarlolmadığını gösterir.

`DEBUGREF_INFO_ALL`\
Bayrakların maskesini gösterir.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar, [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapının hangi alanlarının baş harfe geçirileceğini belirtmek için [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) ve [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) yöntemlerine geçirilir.

`DEBUG_REFERENCE_INFO` Yapının `dwFields` üyesi için hangi alanların kullanıldığını belirtmek için kullanılır ve yapı döndürüldüğünde geçerlidir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
