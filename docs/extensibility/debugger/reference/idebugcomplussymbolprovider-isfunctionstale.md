---
description: Belirtilen hata ayıklama adresli işlevin eski olarak kabul edilir olup olmadığını belirler.
title: IDebugComPlusSymbolProvider::IsFunctionStale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionStale
ms.assetid: dcffc090-4ed8-47b2-ba51-bce1a6b6428d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f160180b9076345612f285df69e64b90f0d442b2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725290"
---
# <a name="idebugcomplussymbolproviderisfunctionstale"></a>IDebugComPlusSymbolProvider::IsFunctionStale
Belirtilen hata ayıklama adresli işlevin eski olarak kabul edilir olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsFunctionStale(
    IDebugAddress* pAddress
);
```

```csharp
int IsFunctionStale(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
[in] [IDebugAddress arabirimiyle temsil edilen hata ayıklama](../../../extensibility/debugger/reference/idebugaddress.md) adresi. Bu adres bir METHOD_ADDRESS.

## <a name="return-value"></a>Dönüş Değeri
İşlev eski olarak kabul edilirse `S_OK` döndürür. İşlev eski yoksa `S_FALSE` döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, **IDebugComPlusSymbolProvider** arabirimini ortaya çıkaran [bir CDebugSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) nesnesi için bu yöntemin nasıl uygulandığını gösterir.

```cpp
HRESULT CDebugSymbolProvider::IsFunctionStale(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionStale );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsFunctionStale( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion ))
    {

        // S_FALSE indicates the function is not stale

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsFunctionStale, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
