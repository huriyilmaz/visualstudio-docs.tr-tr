---
description: Bu kesme noktası isteğinin kesme noktası konum türünü alır.
title: IDebugBreakpointRequest2::GetLocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 888d17e7616162120835ef77cee47a24e149b5cf4902b78b5a819c8f451b6b48
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452284"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
Bu kesme noktası isteğinin kesme noktası konum türünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetLocationType(
    BP_LOCATION_TYPE* pBPLocationType
);
```

```csharp
int GetLocationType(
    out enum_BP_LOCATION_TYPE pBPLocationType
);
```

## <a name="parameters"></a>Parametreler
`pBPLocationType`\
[out] Bu kesme noktası [isteğinin BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) açıklayan bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. `E_FAIL`İlişkili `bpLocation` çalışma alanı yapısında [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) geçerli değilse döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CDebugBreakpointRequest` [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabirimini ortaya çıkaran basit bir nesne için bu yöntemin nasıl uygulandığını gösterir.

```
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)
{
    HRESULT hr;

    if (pBPLocationType)
    {
        // Set default BP_LOCATION_TYPE.
        *pBPLocationType = BPLT_NONE;

        // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.
        if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))
        {
            // Get the new BP_LOCATION_TYPE.
            *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
