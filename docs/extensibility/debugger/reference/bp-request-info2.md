---
description: Satıcı GUID'si, kısıtlama ve izleme noktası dahil olmak üzere bir kesme noktası uygulamak için gereken bilgileri içerir.
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5934c73460cb6256865d431e19765a6518556e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120367"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Satıcı GUID'si, kısıtlama ve izleme noktası dahil olmak üzere bir kesme noktası uygulamak için gereken bilgileri içerir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi alanların doldurulması [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) bir bayrak birleşimi.

`guidLanguage`\
Dil GUID'si.

`bpLocation`\
Kesme [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) türünü belirten bir yapılandırma yapısıdır.

`pProgram`\
Kesme noktası oluşan uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`bstrProgramName`\
Kesme noktası oluşan uygulamanın adı.

`pThread`\
Kesme noktası oluştuğu iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrThreadName`\
Kesme noktası oluşan iş parçacığının adı.

`bpCondition`\
Kesme [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) hangi koşulların altında olduğunu açıklayan bir yapıdır.

`bpPassCount`\
Kesme [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) geçiş sayısı bilgilerini içeren bir yapıdır.

`dwFlags`\
İstenen kesme noktası için [bayrakları](../../../extensibility/debugger/reference/bp-flags.md) belirten BP_FLAGS bayrağının bir birleşimi.

`guidVendor`\
Satıcının GUID'si. Null değer olabilir.

`bstrConstraint`\
Kesme noktası kısıtlaması adı. Null değer olabilir.

`bstrTracepoint`\
İzleme noktasının adı. Null değer olabilir.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetRequestInfo2 yöntemi tarafından](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
