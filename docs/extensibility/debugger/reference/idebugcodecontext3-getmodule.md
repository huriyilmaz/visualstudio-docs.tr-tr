---
title: IDebugCodeContext3::GetModule | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20e4bbc32aef11c91e4f5c642bb48acb26633fe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734203"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Hata ayıklama modülünün arabirimine bir başvuru alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetModule(
    IDebugModule2 **ppModule
);
```

```csharp
public int GetModule(
    out IDebugModule2 ppModule
);
```

## <a name="parameters"></a>Parametreler
`ppModule`\
[çıkış] Hata ayıklama modülü arabirimine başvuru.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) arabirimini ortaya çıkaran bir **CDebugCodeContext** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;

    IfFalseGo( ppModule, E_INVALIDARG );
    *ppModule = NULL;

    IfFailGo( this->GetModule(&pModule) );
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
