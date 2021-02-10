---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d5d4e9ee9808c25bb0df570ac451c061067904c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938765"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Bu yapı, bir kapsam içindeki yerel bir değişkenin adresini temsil eder (genellikle bir işlev veya yöntem).

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
Yöntemin veya yerel değişkenin bir parçası olan işlevin KIMLIĞI.

[C++] `_mdToken` , `typedef` 32 bitlik bir içindir `int` .

`pLocal`\
Bu yapının adresini temsil eden belirteç.

`dwIndex`\
Yöntem veya işlevde bu yerel değişkenin dizini veya başka bir değer (dile özgü) olabilir.

## <a name="remarks"></a>Açıklamalar

Bu yapı, [](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` `DEBUG_ADDRESS_UNION` yapı alanı `ADDRESS_KIND_LOCAL` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından bir değer) olarak ayarlandığında DEBUG_ADDRESS_UNION yapısındaki birleşimin bir parçasıdır.

> [!WARNING]
> [Yalnızca C++] `pLocal` Null değilse, `Release` belirteç işaretçisi üzerinde çağırmanız gerekir ( `addr` [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısındaki bir alandır):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Gereksinimler

Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
