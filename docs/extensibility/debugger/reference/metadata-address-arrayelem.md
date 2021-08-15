---
description: Bu yapı, bir dizi içindeki bir dizi öğesini temsil eder.
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ec0844ce76be009e0111cc5edfc71350f05037d685aaa4d793b7e9446a9b891
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401823"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Bu yapı, bir dizi içindeki bir dizi öğesini temsil eder.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="members"></a>Üyeler

`tokMethod`\
Bu öğenin bir parçası olduğu dizinin kimliği.

[C++] `_mdToken` , `typedef` 32 bit için bir'dır. `int`

`dwIndex`\
Dizi içindeki bu öğenin dizini.

## <a name="remarks"></a>Açıklamalar
Bu yapı, yapının alanı [(DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) enumerasyonundan bir değer) olarak ayarlanırken ADDRESS_KIND `dwKind` parçası `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_ARRAYELEM` olur. [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
