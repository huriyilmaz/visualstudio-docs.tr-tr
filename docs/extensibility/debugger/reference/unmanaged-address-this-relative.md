---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c19109215a9e8824f1648860c39ccb33836ca93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880001"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Bu yapı, bir `this` işaretçiye (Visual Basic) göre bir adresi temsil eder `Me` .

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Üyeler
 `dwOffset`\
 Taban konumundan bayt konumu (örneğin, bir sınıf vtable 'u başlangıcı).

 `dwBitOffset`\
 Taban konumundan bit cinsinden konum (bir bit alanına başvurmadığı takdirde daima 0).

 `dwBitLength`\
 Adresi temsil eden bit sayısı (bir bit alanına başvurmadığı müddetçe daima 0).

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` `DEBUG_ADDRESS_UNION` yapı alanı `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından bir değer) olarak ayarlandığında DEBUG_ADDRESS_UNION yapısındaki birleşimin bir parçasıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
