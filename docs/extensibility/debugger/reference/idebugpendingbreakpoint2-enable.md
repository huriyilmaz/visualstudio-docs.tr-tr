---
description: Bekleyen kesme noktasının etkin durumunu değiştirir.
title: 'IDebugPendingBreakpoint2:: Enable | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3d0e92cf469a48e2ace84861a36cb256835d4cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169931"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Bekleyen kesme noktasının etkin durumunu değiştirir.

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
'ndaki `TRUE`Bekleyen bir kesme noktasını etkinleştirmek için () sıfır dışında (), devre dışı bırakmak için sıfır () olarak ayarlayın `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_BP_DELETED`Kesme noktasının silinip silinmediğini döndürür.

## <a name="remarks"></a>Açıklamalar
Bekleyen bir kesme noktası etkinleştirildiğinde veya devre dışı bırakıldığında, onunla bağlantılı tüm kesme noktaları aynı duruma ayarlanır.

Kesme noktası zaten etkinleştirilmiş veya devre dışı bırakılmış olsa bile, bu yöntem gerektiği kadar çok kez çağrılabilir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

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
