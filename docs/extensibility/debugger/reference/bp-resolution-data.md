---
title: BP_RESOLUTION_DATA | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737846"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Veri kesme noktasını bağlamanın sonucunu açıklar.

## <a name="syntax"></a>Sözdizimi

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
Bağlanan veri ifadesi.

`bstrFunc`\
Veri kesme noktasının bağlı olduğu işlevin adı (varsa).

`bstrImage`\
Veri kesme noktasının bağlı olduğu modülün adı (MyModule.dll, örneğin).

`dwFlags`\
Veri kesme noktasının nasıl uygulandığını açıklayan [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) numaralandırmadeğeri.

## <a name="remarks"></a>Açıklamalar
Bu [yapı,](../../../extensibility/debugger/reference/bp-resolution-location.md) [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) yöntemi yle döndürülen [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapının bir üyesi olan BP_RESOLUTION_LOCATION yapının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
