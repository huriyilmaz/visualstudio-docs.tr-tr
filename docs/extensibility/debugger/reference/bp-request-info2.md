---
description: Satıcı GUID, kısıtlama ve izleme noktası dahil bir kesme noktası uygulamak için gereken bilgileri içerir.
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1efeceb42d45822f232e5a2e5e2fbe33f9996e34
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144123"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Satıcı GUID, kısıtlama ve izleme noktası dahil bir kesme noktası uygulamak için gereken bilgileri içerir.

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
[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.

`guidLanguage`\
Dil GUID 'SI.

`bpLocation`\
Kesme noktası konumunun türünü belirten [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısı.

`pProgram`\
Kesme noktasının gerçekleştiği uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`bstrProgramName`\
Kesme noktasının gerçekleştiği uygulamanın adı.

`pThread`\
Kesme noktasının gerçekleştiği iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrThreadName`\
Kesme noktasının gerçekleştiği iş parçacığının adı.

`bpCondition`\
Kesme noktasının tetikleneceği koşulları açıklayan [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) yapısı.

`bpPassCount`\
Kesme noktasının geçiş sayısı bilgilerini içeren [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) yapısı.

`dwFlags`\
İstenen kesme noktasına yönelik bayrakları belirten [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) numaralandırmasındaki bayrakların birleşimi.

`guidVendor`\
Satıcının GUID 'SI. Null bir değer olabilir.

`bstrConstraint`\
Kesme noktası kısıtlamasının adı. Null bir değer olabilir.

`bstrTracepoint`\
İzleme noktasının adı. Null bir değer olabilir.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

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
