---
description: Bir kod kesme noktasının konumunu açıklar.
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca265d73cf54ce04f4ef3c25ee52ace94d269074
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059606"
---
# <a name="bp_resolution_code"></a>BP_RESOLUTION_CODE
Bir kod kesme noktasının konumunu açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_CODE {
    IDebugCodeContext2* pCodeContext;
} BP_RESOLUTION_CODE;
```

```csharp
public struct BP_RESOLUTION_CODE {
    public IDebugCodeContext2 pCodeContext;
};
```

## <a name="members"></a>Üyeler
`pCodeContext`\
Koddaki kesme noktasının konumunu tanımlayan [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) yöntemi tarafından döndürülen [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapısının bir üyesini döndüren [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) yapısının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
