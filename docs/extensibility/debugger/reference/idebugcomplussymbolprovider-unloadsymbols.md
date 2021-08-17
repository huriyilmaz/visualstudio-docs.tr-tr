---
description: Belirtilen modülün hata ayıklama sembollerini bellekten kaldırır.
title: 'IDebugComPlusSymbolProvider:: UnloadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b57c4f9c0e58e8757ee7b2e89ed7e6e35337e5eca4fcbd7bf66bd55be39eefa7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342407"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Belirtilen modülün hata ayıklama sembollerini bellekten kaldırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int UnloadSymbols(
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
'ndaki Uygulama etki alanının tanımlayıcısı.

`guidModule`\
'ndaki Modülün benzersiz tanıtıcısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugSymbolProvider::UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pmodule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );

#if DEBUG

    DebugVerifyModules();
#endif

    IfFailGo( GetModule( idModule, &pmodule ) );

#if DEBUG

    DebugVerifyModules();
#endif

    RemoveModule( pmodule );
    pmodule->Cleanup();

Error:
#if DEBUG

    DebugVerifyModules();
#endif

    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
