---
title: GETNAME_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736665"
---
# <a name="getname_type"></a>GETNAME_TYPE
Alınacak dosyaların ad türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Alanlar
`GN_NAME`\
Belgenin veya bağlamın dostane bir adını belirtir.

`GN_FILENAME`\
Belgenin veya bağlamın tam yolunu belirtir.

`GN_BASENAME`\
Belgenin veya bağlamın tam yolu yerine temel dosya adını belirtir.

`GN_MONIKERNAME`\
Belgenin veya bağlamın benzersiz bir adını bir takma ad biçiminde belirtir.

`GN_URL`\
Belgenin veya bağlamın URL adını belirtir.

`GN_TITLE`\
Varsa belgenin bir başlığını belirtir.

`GN_STARTPAGEURL`\
İşlemler için başlangıç sayfası URL'sini alır.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [getname, GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)ve [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)yöntemlerine ne tür bir ad verilecek belirtilmek için parametre olarak geçirilir. [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
