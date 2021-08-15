---
description: Bu yapı bir yöntemin veya işlevin parametresini temsil eder.
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
ms.openlocfilehash: dabcf2b31de54a5a344eaf795798e05d84bdb282b949c6b5c2b50e78a8f37f27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276236"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Bu yapı bir yöntemin veya işlevin parametresini temsil eder.

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
 Parametresinin bir parçası olduğu yöntemin KIMLIĞI.

 `tokParam`\
 Parametrenin KIMLIĞI.

 `dwIndex`\
 Parametre listesindeki parametresinin dizini.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` `DEBUG_ADDRESS_UNION` yapı alanı `ADDRESS_KIND_PARAM` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından bir değer) olarak ayarlandığında DEBUG_ADDRESS_UNION yapısındaki birleşimin bir parçasıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
