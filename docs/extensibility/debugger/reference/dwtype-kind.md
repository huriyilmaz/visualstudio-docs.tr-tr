---
description: IDebugField nesnesinin türünü yorumlamayı belirtir.
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71579d77883246e4dd945276668eb2ca3ed26205
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127616"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinin türünü yorumlamayı belirtir.

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
Bu [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) bir yapı olarak [yorumlanması](../../../extensibility/debugger/reference/metadata-type.md) METADATA_TYPE gerekir.

`TYPE_KIND_PDB`\
Bu `TYPE_INFO` birliktelik, bir PDB_TYPE [yorumlanır.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
Bu `TYPE_INFO` birliktelik, bir BUILT_TYPE [yorumlanır.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Açıklamalar
Bu numaralama değerlerinin değeri, TYPE_INFO yapısının alanında görünür ve birliğin `dwKind` üyesinin nasıl [](../../../extensibility/debugger/reference/type-info.md) yorumlanmasına karar `type` verir. Yapı, `TYPE_INFO` [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemine yapılan bir çağrıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
