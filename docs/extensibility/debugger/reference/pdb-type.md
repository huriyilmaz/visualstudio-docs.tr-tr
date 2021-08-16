---
description: Bu yapı, PDB simgesinden alınan alan türüyle ilgili bilgileri belirtir.
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b2a812fa59c8017b6a4296d0172fc2225d099470685450c50e2c618b6bd66f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415175"
---
# <a name="pdb_type"></a>PDB_TYPE

Bu yapı, PDB simgesinden alınan alan türüyle ilgili bilgileri belirtir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Üyeler

`ulAppDomainID`\
Sembolün geldiği uygulamanın kimliği. Bu, uygulamanın bir örneğini benzersiz olarak tanımlamak için kullanılır.

`guidModule`\
Bu alanı içeren modülün GUID'si.

`symid`\
Bu alana karşılık gelen sembolün kimliği.

## <a name="remarks"></a>Açıklamalar

Bu yapı, yapının alanı olarak [(TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) enumerasyonundan bir değer) ayarlanırken dwTYPE_KIND `dwKind` olarak `TYPE_INFO` `TYPE_KIND_PDB` görünür. [](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Gereksinimler

Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
