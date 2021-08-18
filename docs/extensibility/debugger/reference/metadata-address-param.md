---
description: Bu yapı, bir yöntemin veya işlevin parametresini temsil eder.
title: METADATA_ADDRESS_PARAM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2a160789b4b5e19ffd6e9eb1974f85396b2d8f4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103123"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Bu yapı, bir yöntemin veya işlevin parametresini temsil eder.

## <a name="syntax"></a>Syntax

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
 parametresinin bir parçası olduğu yöntemin kimliği.

 `tokParam`\
 Parametrenin kimliği.

 `dwIndex`\
 Parametre listesinde parametre dizini.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, yapının alanı [(DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) enumerasyonundan bir değer) olarak ayarlanırken ADDRESS_KIND `dwKind` parçası `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_PARAM` olur. [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
