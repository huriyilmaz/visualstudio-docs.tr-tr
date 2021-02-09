---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 541f8b51d4ce56b167abd3ecdb28d08bec0c02c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891273"
---
# <a name="getname_type"></a>GETNAME_TYPE
Alınacak dosyaların ad türünü belirtir.

## <a name="syntax"></a>Syntax

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
Belge veya bağlamın kolay bir adını belirtir.

`GN_FILENAME`\
Belgenin veya bağlamın tam yolunu belirtir.

`GN_BASENAME`\
Belge veya bağlamın tam yolu yerine bir temel dosya adı belirtir.

`GN_MONIKERNAME`\
Bir ad biçiminde belge veya bağlamın benzersiz bir adını belirtir.

`GN_URL`\
Belge veya bağlamın URL adını belirtir.

`GN_TITLE`\
Bir belge varsa, belgenin bir başlığını belirtir.

`GN_STARTPAGEURL`\
İşlem için başlangıç sayfası URL 'sini alır.

## <a name="remarks"></a>Açıklamalar
Bu değerler, döndürülecek ad türünü belirtmek için [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)ve [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) yöntemlerine parametre olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
