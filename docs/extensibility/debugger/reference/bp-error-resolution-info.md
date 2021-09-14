---
description: Konum, program ve iş parçacığı dahil olmak üzere bir hata kesme noktası çözümlemesi açıklar.
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e678d3089032d93eb2974123d9a5c2153c97e95
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725824"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Konum, program ve iş parçacığı dahil olmak üzere bir hata kesme noktası çözümlemesi açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Bu yapının hangi [alanlarının BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) belirten bir veri BPERESI_FIELDS değerleri birleşimi.

`bpResLocation`\
Kesme [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) konumunu belirten veri birliliği.

`pProgram`\
Kesme noktası hatasının meydana geldiği uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`pThread`\
Kesme noktası hatasını oluşturan uygulamanın üzerinde çalıştır olduğu iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrMessage`\
Bu hata çözümlemesi sonucunda ortaya çıkan herhangi bir uyarı veya hata iletisini içeren bir dize.

`dwType`\
Kesme noktası [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) belirten bir değerdir.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetResolutionInfo yönteminden](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
