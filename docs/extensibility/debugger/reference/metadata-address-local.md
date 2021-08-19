---
description: Bu yapı, bir kapsam içindeki yerel değişkenin adresini (genellikle bir işlev veya yöntem) temsil eder.
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71b8b4ef578646a63ec64fbbde506dd71984fe35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042822"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Bu yapı, bir kapsam içindeki yerel değişkenin adresini (genellikle bir işlev veya yöntem) temsil eder.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Üyeler

`tokMethod`\
Yöntemin veya işlevin kimliği, yerel değişkenin bir parçası.

[C++] `_mdToken` , `typedef` 32 bit için bir'dır. `int`

`pLocal`\
Bu yapının adresini temsil eden belirteç.

`dwIndex`\
Bu yerel değişkenin yönteminde veya işlevinde dizini veya başka bir değer (dile özgü) olabilir.

## <a name="remarks"></a>Açıklamalar

Bu yapı, yapının alanı [(DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) enumerasyonundan bir değer) olarak ayarlanırken ADDRESS_KIND `dwKind` parçası `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_LOCAL` olur. [](../../../extensibility/debugger/reference/address-kind.md)

> [!WARNING]
> [yalnızca C++ ] null `pLocal` ise, belirteç işaretçisi üzerinde çağrısı `Release` `addr` DEBUG_ADDRESS: [](../../../extensibility/debugger/reference/debug-address.md)
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Gereksinimler

Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
