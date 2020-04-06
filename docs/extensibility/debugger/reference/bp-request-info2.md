---
title: BP_REQUEST_INFO2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737886"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Satıcı GUID, kısıtlama ve izleme noktası da dahil olmak üzere bir kesme noktası uygulamak için gereken bilgileri içerir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _BP_REQUEST_INFO2 {
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
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
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
Hangi alanların [doldurulduğuna](../../../extensibility/debugger/reference/bpreqi-fields.md) BPREQI_FIELDS numaralandırmadan gelen bayrakların birleşimi.

`guidLanguage`\
Dil GUID.

`bpLocation`\
Kesme noktası konumunun türünü belirten [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapı.

`pProgram`\
Kesme noktasının oluştuğu uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`bstrProgramName`\
Kesme noktasının oluştuğu uygulamanın adı.

`pThread`\
Kesme noktasının oluştuğu iş parçacığı temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrThreadName`\
Kesme noktasının oluştuğu iş parçacığının adı.

`bpCondition`\
Kırılma noktasının hangi koşullar altında ateş edeceğini açıklayan [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) yapı.

`bpPassCount`\
Kesme noktasının geçiş sayısı bilgilerini içeren [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) yapı.

`dwFlags`\
İstenen kesme noktası için bayrakları belirten [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) numaralandırmadan gelen bayrakların birleşimi.

`guidVendor`\
Satıcının GUID. Null bir değer olabilir.

`bstrConstraint`\
Kesme noktası kısıtlamasının adı. Null bir değer olabilir.

`bstrTracepoint`\
İz noktasının adı. Null bir değer olabilir.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) yöntemi ile döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

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
