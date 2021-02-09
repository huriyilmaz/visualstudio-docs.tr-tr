---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e13d02cb08f957636a81bf4a985f1d7006b6c2ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908096"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinin türünün nasıl yorumlanacağını belirtir.

## <a name="syntax"></a>Syntax

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
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) UNION [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) yapısı olarak yorumlanmalıdır.

`TYPE_KIND_PDB`\
`TYPE_INFO`Birleşim [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) yapısı olarak yorumlanmalıdır.

`TYPE_KIND_BUILT`\
`TYPE_INFO`Birleşim [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) yapısı olarak yorumlanmalıdır.

## <a name="remarks"></a>Açıklamalar
Bu sabit listesinin değerleri `dwKind` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısı alanında görünür ve UNION üyesini nasıl yorumlayacağınız tespit etmek için kullanılır `type` . `TYPE_INFO`Yapı, [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemi çağrısıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
