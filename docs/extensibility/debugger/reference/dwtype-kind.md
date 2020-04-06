---
title: dwTYPE_KIND | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737188"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[Bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinin türünü nasıl yorumlanacağı belirtilir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Alanlar
`TYPE_KIND_METADATA`\
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) birliği [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) bir yapı olarak yorumlanmalıdır.

`TYPE_KIND_PDB`\
Birlik `TYPE_INFO` [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) bir yapı olarak yorumlanmalıdır.

`TYPE_KIND_BUILT`\
`TYPE_INFO` Birlik, [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) bir yapı olarak yorumlanmalıdır.

## <a name="remarks"></a>Açıklamalar
Bu numaralandırmanın değerleri [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısı `dwKind` alanında görünür ve sendika üyesinin nasıl `type` yorumlandığını belirlemek için kullanılır. Yapı `TYPE_INFO` [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemine bir çağrı ile döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
