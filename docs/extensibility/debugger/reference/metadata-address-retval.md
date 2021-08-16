---
description: Bu yapı bir yöntem veya işlevden döndürülen değeri temsil eder.
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a323d934cceff20b5e89215dfb9a6d49020a707e07f5d3ca5f37a5fe189627c2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377294"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Bu yapı bir yöntem veya işlevden döndürülen değeri temsil eder.

## <a name="syntax"></a>Syntax

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
 Bu dönüş değerinin için olan metodun KIMLIĞI.

 `dwCorType`\
 Dönüş değerinin temel türü. bu, `CorElementType` .NET Framework SDK corhdr. h dosyasında tanımlanan numaralandırmadaki bir değerdir.

 `dwSigSize`\
 Dönüş değeri imzasının boyutu (içinde depolanan `rgSig` ).

 `rgSig`\
 Dönüş değerinin imzasını oluşturan bir bayt dizisi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` `DEBUG_ADDRESS_UNION` yapı alanı `ADDRESS_KIND_RETVAL` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından bir değer) olarak ayarlandığında DEBUG_ADDRESS_UNION yapısındaki birleşimin bir parçasıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
