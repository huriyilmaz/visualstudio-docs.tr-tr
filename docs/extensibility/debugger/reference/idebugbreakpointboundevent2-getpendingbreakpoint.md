---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 85c137445e2255a76f7fa3be2fb56e2579e578c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735258"
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Bağlanmakta olan bekleyen kesme noktasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```cpp
int GetPendingBreakpoint(
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parametreler
`ppPendingBP`\
[çıkış] Bekleyen kesme noktasının bağlanmasını temsil eden [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) arabirimini ortaya çıkaran bir **CBreakpointSetDebugEventBase** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(
    IDebugPendingBreakpoint2 **ppPendingBP)
{
    HRESULT hRes = E_FAIL;

    if ( ppPendingBP )
    {
        if ( m_pPendingBP )
        {
            *ppPendingBP = m_pPendingBP;

            m_pPendingBP->AddRef();

            hRes = S_OK;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
