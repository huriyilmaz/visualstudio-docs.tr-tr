---
description: Bir derlemenin bulunduğu yeri belirtir.
title: ASSEMBLYLOCRESOLUTION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6756d3c0ee996c0fca2eb35ff92c552f750f2817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144630"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Bir derlemenin bulunduğu yeri belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Alanlar
`ALR_NAME`\
Derleme, geçerli ad alanında bulunur.

`ALR_USERDIR`\
Derleme bir kullanıcı dizininde bulunur.

`ALR_SHAREDDIR`\
Derleme, paylaşılan dizinde bulunur.

`ALR_REMOTEDIR`\
Derleme uzak bir dizinde bulunur.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [Resolveassemblyref](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) ve [Getmanagedviewercreationdata](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) yöntemleri tarafından döndürülür.

Bu değerler `OR` işlemle birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
