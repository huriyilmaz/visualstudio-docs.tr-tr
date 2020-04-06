---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731123"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Hata ayıklama altyapısında (DE) bekleyen bir kesme noktası oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parametreler
`pBPRequest`\
[içinde] Oluşturulacak bekleyen kesme noktasını açıklayan bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) nesnesi.

`ppPendingBP`\
[çıkış] Bekleyen kesme noktasını temsil eden bir [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Parametre geçersiz veya eksikse DE tarafından desteklenen herhangi bir `pBPRequest` dil eşleşmiyorsa genellikle döndürür. `E_FAIL` `pBPRequest`

## <a name="remarks"></a>Açıklamalar
Bekleyen kesme noktası, bir kesme noktasını koda bağlamak için gereken tüm bilgilerin bir koleksiyonudur. Bu yöntemden döndürülen bekleyen kesme [noktası, Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi çağrılana kadar koda bağlı değildir.

Bekleyen her kesme noktası için kullanıcı kümelenir, oturum hata ayıklama yöneticisi (SDM) ekli her DE bu yöntemi çağırır. Kesme noktasının o DE'de çalışan programlar için geçerli olduğunu doğrulamak DE'ye kade olur.

Kullanıcı bir kod satırında bir kesme noktası ayarladığında, DE kesme noktasını belgede bu koda karşılık gelen en yakın satıra bağlamak için serbesttir. Bu, kullanıcının çok satırlı bir deyimin ilk satırında bir kesme noktası ayarlamasını, ancak son satıra bağlamasını (tüm kodun hata ayıklama bilgilerinde atfedildiği) mümkün kılar.

## <a name="example"></a>Örnek
Aşağıdaki örnek, basit `CProgram` bir nesne için bu yöntemin nasıl uygulanacağını gösterir. De'nin uygulanması daha `IDebugEngine2::CreatePendingBreakpoint` sonra her programda yöntemin bu uygulanması için tüm çağrıları iletebilir.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bağla](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
