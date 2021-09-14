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
ms.openlocfilehash: ae93e6438c476ce34a6287ba2f35bf6a78e6ac2a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634705"
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
 Bu yapı, yapının alanı [(DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) enumerasyonundan bir değer) olarak ayarlanırken ADDRESS_KIND `dwKind` parçası `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` olur. [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
