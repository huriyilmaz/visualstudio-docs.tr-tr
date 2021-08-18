---
description: Alınan dosyaların ad türünü belirtir.
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b95c08ab5adc5140bfcfc21b9e9fa7cc9f46c78a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065000"
---
# <a name="getname_type"></a>GETNAME_TYPE
Alınan dosyaların ad türünü belirtir.

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
Belgenin veya bağlamın kolay adını belirtir.

`GN_FILENAME`\
Belgenin veya bağlamın tam yolunu belirtir.

`GN_BASENAME`\
Belgenin veya bağlamın tam yolu yerine temel dosya adını belirtir.

`GN_MONIKERNAME`\
Belgenin veya bağlamın benzersiz bir adını bilinen ad olarak belirtir.

`GN_URL`\
Belgenin veya bağlamın URL adını belirtir.

`GN_TITLE`\
Varsa belgenin başlığını belirtir.

`GN_STARTPAGEURL`\
İşlemler için başlangıç sayfası URL'sini alır.

## <a name="remarks"></a>Açıklamalar
Bu değerler, ne tür bir ad getirilsin belirtmek için [GetName,](../../../extensibility/debugger/reference/idebugdocument2-getname.md) [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)ve [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) yöntemlerine parametre olarak geçirilsin.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
