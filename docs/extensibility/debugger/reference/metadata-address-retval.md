---
title: METADATA_ADDRESS_RETVAL | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714267"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Bu yapı, bir yöntem veya işlevden gelen bir geri dönüş değerini temsil eder.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Üyeler
 `tokMethod`\
 Bu iade değerinin olduğu yöntemin kimliği.

 `dwCorType`\
 Temel getiri değeri türü. Bu, .NET `CorElementType` Framework SDK corhdr.h dosyasında tanımlanan numaralandırmadan alınan bir değerdir.

 `dwSigSize`\
 İade değeri imzasının boyutu (depolanan `rgSig`gibi).

 `rgSig`\
 İade değerinin imzasını oluşturan bir bayt dizisi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, `DEBUG_ADDRESS_UNION` yapı alanı [(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmadan bir değer) `ADDRESS_KIND_RETVAL` `dwKind` ayarlandığında, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapıdaki birliğin bir parçasıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
