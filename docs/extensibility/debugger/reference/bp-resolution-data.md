---
description: Bir veri kesme noktası bağlamanın sonucundan açıklar.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82ede309d0483dfc406dc54444975ae4cc8afa9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635233"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Bir veri kesme noktası bağlamanın sonucundan açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Üyeler
`bstrDataExpr`\
Bağlı olan veri ifadesi.

`bstrFunc`\
Veri kesme noktası bağlı işlevin adı (varsa).

`bstrImage`\
Veri kesme noktası tarafından MyModule.dll modül adı (örneğin, modülün adı).

`dwFlags`\
Veri kesme [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) açıklayan bir değerdir.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [getresolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) döndürülen BP_RESOLUTION_INFO yapısının bir [](../../../extensibility/debugger/reference/bp-resolution-info.md) üyesi olan BP_RESOLUTION_LOCATION üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
