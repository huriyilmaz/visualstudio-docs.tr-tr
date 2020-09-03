---
title: 'IDebugComPlusSymbolProvider:: Lacesymbir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ReplaceSymbols
- IDebugComPlusSymbolProvider::ReplaceSymbols
ms.assetid: 82fbc8db-c4b1-432f-bec9-1a9dc09570be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90ef0ae096618b776182b397d196f2a4477abe5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733609"
---
# <a name="idebugcomplussymbolproviderreplacesymbols"></a>IDebugComPlusSymbolProvider::ReplaceSymbols
Geçerli hata ayıklama sembollerini, belirtilen veri akışındaki verilerle değiştirir.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT ReplaceSymbols(
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    IStream* pStream
);
```

```csharp
int ReplaceSymbols(
    uint    ulAppDomainID,
    Guid    guidModule,
    IStream pStream
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
'ndaki Uygulama etki alanının tanımlayıcısı.

`guidModule`\
'ndaki Modülün benzersiz tanıtıcısı.

`pStream`\
'ndaki Yeni sembolleri içeren veri akışı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugSymbolProvider::ReplaceSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pStream
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::ReplaceSymbols );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->ReplaceSymbols( pStream ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::ReplaceSymbols, hr );
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
