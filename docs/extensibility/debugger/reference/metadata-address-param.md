---
title: METADATA_ADDRESS_PARAM | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0319cfc6f2be817a25126e67cdc470bc727a4ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714439"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Bu yapı, bir yöntem veya işlevin parametresini temsil eder.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Üyeler
 `tokMethod`\
 Parametrenin parçası olduğu yöntemin kimliği.

 `tokParam`\
 Parametrenin kimliği.

 `dwIndex`\
 Parametrenin parametre dizini bir parametre listesinde.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, `DEBUG_ADDRESS_UNION` yapı alanı [(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmadan bir değer) `ADDRESS_KIND_PARAM` `dwKind` ayarlandığında, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapıdaki birliğin bir parçasıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
