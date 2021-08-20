---
description: Bir kesme noktası uygulamak için gereken bilgileri içerir.
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe85c279173932adc3ccc4dab98cc5b0727d1b3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145893"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Bir kesme noktası uygulamak için gereken bilgileri içerir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetRequestInfo yöntemi tarafından](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) döndürülür.

Hata ayıklama altyapısı satıcısı GUID'si, kesme noktası kısıtlaması veya izleme noktası elde etmek için bkz. [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) bakın.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
