---
description: Bu BUILT_TYPE, meta verilerden alınan alan türüyle ilgili bilgileri belirtir.
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81b18a6e238b71a7c91445b551beb34dd081e53c24b5301cd58c495a04e1e733
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360969"
---
# <a name="built_type"></a>BUILT_TYPE
Bu yapı, meta verilerden alınan alan türüyle ilgili bilgileri belirtir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Üyeler
`ulAppDomainID`\
Sembolün geldiği uygulamanın kimliği. Bu, uygulamanın bir örneğini benzersiz olarak tanımlamak için kullanılır.

`guidModule`\
Bu alanı içeren modülün GUID'si.

`pUnderlyingField`\
Bu yerleşik alanla ilişkili temel alanı tanımlayan [bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, yapının alanı olarak [(TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) enumerasyonundan bir değer) ayarlanırken dwTYPE_KIND `dwKind` olarak `TYPE_INFO` `TYPE_KIND_BUILT` görünür. [](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
