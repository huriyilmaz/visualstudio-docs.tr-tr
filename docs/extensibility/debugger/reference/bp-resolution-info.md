---
description: Bir kod kesme noktası veya veri kesme noktası için bağlı kesme noktası bilgilerini açıklar.
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a47f081b7fcd2f1d61c23654446566196cfccd1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120289"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Bir kod kesme noktası veya veri kesme noktası için bağlı kesme noktası bilgilerini açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi alanların doldurulması [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) bir bayrak koleksiyonu.

`bpResLocation`\
Kod [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) verilerde kesme noktası konumunu belirten bir yapılandırma yapısıdır.

`pProgram`\
Kesme noktası hatasının meydana geldiği uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`pThread`\
Kesme noktası hatasını içeren uygulamanın çalıştır olduğu iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetResolutionInfo tarafından döndürülür.](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
