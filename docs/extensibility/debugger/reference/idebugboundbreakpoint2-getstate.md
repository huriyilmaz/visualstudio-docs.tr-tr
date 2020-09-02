---
title: 'IDebugBoundBreakpoint2:: GetState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugBoundBreakpoint2::GetState method
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30e36880fda8b94eefcbe8b3110685b2114476a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735481"
---
# <a name="idebugboundbreakpoint2getstate"></a>IDebugBoundBreakpoint2::GetState
Bu bağlantılı kesme noktasının durumunu alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetState( 
    BP_STATE* pState
);
```

```csharp
int GetState( 
    out enum_BP_STATE pState
);
```

## <a name="parameters"></a>Parametreler
`pState`\
dışı Kesme noktasının durumunu açıklayan [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CBoundBreakpoint` [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)
{
    HRESULT hr;

    // Check for a valid pointer to pState and assign the local state variable.
    if (pState)
    {
        *pState = m_state;
        hr = S_OK;
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
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
