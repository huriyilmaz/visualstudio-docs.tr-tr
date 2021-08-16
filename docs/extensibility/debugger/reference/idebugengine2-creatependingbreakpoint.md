---
description: Hata ayıklama altyapısında (DE) bekleyen bir kesme noktası oluşturur.
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9088fdc05142faca79a4d2f6b31a76b2344c7800c6920cc19927486c01957ae7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307836"
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
'ndaki Oluşturulacak bekleyen kesme noktasını açıklayan bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) nesnesi.

`ppPendingBP`\
dışı Bekleyen kesme noktasını temsil eden bir [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Genellikle parametresi `E_FAIL` `pBPRequest` , `pBPRequest` parametresi geçersiz veya eksik ise öğesinin tarafından desteklenen herhangi bir dille eşleşmezse döndürür.

## <a name="remarks"></a>Açıklamalar
Bekleyen bir kesme noktası aslında koda bir kesme noktası bağlamak için gereken tüm bilgilerin bir koleksiyonudur. Bu yöntemden döndürülen bekleyen kesme noktası, [bağlama](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi çağrılana kadar koda bağlı değildir.

Kullanıcı kümelerinin bekleyen her bir kesme noktası için, oturum hata ayıklama Yöneticisi (SDM), her bir ekli de bu yöntemi çağırır. Kesme noktasının, bu de çalıştıran programlar için geçerli olduğunu doğrulamak için DE vardır.

Kullanıcı bir kod satırında bir kesme noktası ayarladığında, kesme noktasını bu koda karşılık gelen belgedeki en yakın çizgiye bağlamak için DE serbest bırakılır. Bu, kullanıcının çok satırlı bir deyimin ilk satırında bir kesme noktası ayarlaması, ancak bunu son satıra bağlama (tüm kodun hata ayıklama bilgilerinde bulunduğu yer) için mümkün hale getirir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir `CProgram` . Uygulamasının uygulamasının uygulanması, her bir `IDebugEngine2::CreatePendingBreakpoint` programda yönteminin bu uygulamasına tüm çağrıları iletebilir.

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
- [Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
