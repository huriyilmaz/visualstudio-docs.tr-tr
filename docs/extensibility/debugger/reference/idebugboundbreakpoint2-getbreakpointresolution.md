---
description: Bu kesme noktasını açıklayan kesme noktası çözünürlüğünü alır.
title: 'IDebugBoundBreakpoint2:: GetBreakpointResolution | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 624a62d1fd582f10ba674ef8a3a03151e487a33960959c68c2abccd2c87e0b5f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360709"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Bu kesme noktasını açıklayan kesme noktası çözünürlüğünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Parametreler
`ppBPResolution`\
dışı Aşağıdakilerden birini temsil eden [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) arabirimini döndürür:

- Kod kesme noktasının bağlandığı koddaki konumu açıklayan kesme noktası çözümleme nesnesi.

- Bir veri kesme noktasının bağlandığı veri konumu.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. , `E_BP_DELETED` Bağlantılı kesme noktası nesnesinin durumunun `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) sabit listesinin parçası) olarak ayarlanmış olup olmadığını döndürür.

## <a name="remarks"></a>Açıklamalar
Kesme noktası çözümlemenin kod veya veri için olup olmadığını anlamak için [Getbreakpointtype](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) metodunu çağırın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CBoundBreakpoint` [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
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
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
