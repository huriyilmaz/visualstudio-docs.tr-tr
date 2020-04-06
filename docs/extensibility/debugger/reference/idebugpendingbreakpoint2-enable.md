---
title: IDebugPendingBreakpoint2::Etkinleştir | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f796aef9533e3861a870b0a0543ae6b4aeb11de1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725896"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Bekleyen kesme noktasının etkin durumunu geçişe savuruyor.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable(
    int fEnable
);
```

## <a name="parameters"></a>Parametreler
`fEnable`\
[içinde] Bekleyen bir kesme`TRUE`noktasını etkinleştirmek için sıfıra () veya devre dışı bırakılabilmek için sıfıra (`FALSE`) ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Kesme `E_BP_DELETED` noktası silinmişse döndürür.

## <a name="remarks"></a>Açıklamalar
Bekleyen bir kesme noktası etkinleştirildiğinde veya devre dışı bırakıldığında, ondan bağlanan tüm kesme noktaları aynı duruma ayarlanır.

Kesme noktası zaten etkin veya devre dışı bırakılmış olsa bile, bu yöntem gerektiği kadar çağrılabilir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimini ortaya çıkaran basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the bound breakpoint member variable is valid, then enable or
        // disable the bound breakpoint.
        if (m_pBoundBP)
        {
            m_pBoundBP->Enable(fEnable);
        }
        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to enabled or disabled depending on the passed BOOL condition.
        m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;
        hr = S_OK;

    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
