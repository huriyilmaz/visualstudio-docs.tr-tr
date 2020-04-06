---
title: METADATA_ADDRESS_LOCAL | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714484"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Bu yapı, bir kapsam içindeki yerel bir değişkenin adresini (genellikle bir işlev veya yöntem) temsil eder.

## <a name="syntax"></a>Sözdizimi

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
Yöntemin veya işlevin kimliği yerel değişkenin bir parçasıdır.

[C++] `_mdToken` 32-bit `typedef` `int`için bir .

`pLocal`\
Bu yapının adresini temsil eden belirteç.

`dwIndex`\
Yöntem veya işlevde bu yerel değişkenin dizini veya başka bir değer (dile özgü) olabilir.

## <a name="remarks"></a>Açıklamalar

Bu yapı, `DEBUG_ADDRESS_UNION` yapı alanı [(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmadan bir değer) `ADDRESS_KIND_LOCAL` `dwKind` ayarlandığında, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapıdaki birliğin bir parçasıdır.

> [!WARNING]
> [Yalnızca C++ ] Null `pLocal` değilse, o zaman `Release` belirteç işaretçisi`addr` [(DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısında bir alandır) çağırmak gerekir:
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Gereksinimler

Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
