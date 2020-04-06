---
title: BP_RESOLUTION_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70e66a936ec1eaf1f818ad249aa4eb14b0b63749
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737833"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Kod kesme noktası veya veri kesme noktası için bağlı kesme noktası bilgilerini açıklar.

## <a name="syntax"></a>Sözdizimi

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
Hangi alanların [doldurulduğuna](../../../extensibility/debugger/reference/bpresi-fields.md) BPRESI_FIELDS oluşan bir bayrak koleksiyonu.

`bpResLocation`\
Parola veya verilerdeki kesme noktasının konumunu belirten [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) yapı.

`pProgram`\
Kesme noktası hatasının oluştuğu uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`pThread`\
Kesme noktası hatasını içeren uygulamanın çalıştırıldığı iş parçacığı temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
