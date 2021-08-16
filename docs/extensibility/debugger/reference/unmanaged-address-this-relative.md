---
description: Bu yapı, bu işaretçiye göre bir adresi temsil eder (Visual Basic).
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f345b94ca9d4bfedef6601273bd74225711f9ef2582abe70eb380ac6cb0328b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414941"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Bu yapı, bir işaretçiye göreli bir adresi temsil `this` eder ( `Me` Visual Basic).

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
 Temel konumdan (örneğin, bir sınıf vtable'ın başlangıcı) byte uzaklığı.

 `dwBitOffset`\
 Bir temel konumdan bitler arasında uzaklık (bit alanına başvurulmadıkça her zaman 0).

 `dwBitLength`\
 Adresi temsil eden bit sayısı (bit alanına başvurulmadıkça her zaman 0).

## <a name="remarks"></a>Açıklamalar
 Bu yapı, yapının alanı [(DEBUG_ADDRESS_UNION ADDRESS_KIND](../../../extensibility/debugger/reference/debug-address-union.md) enumerasyonundan bir değer) olarak ayarlanırken ADDRESS_KIND `dwKind` `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` parçasıdır. [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
