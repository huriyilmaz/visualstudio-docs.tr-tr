---
description: Uygulama etki alanı tanımlayıcısı verilen belirtilen modül için hata ayıklama simgelerinin yüklenip yüklenmediğini belirler.
title: 'IDebugComPlusSymbolProvider:: AreSymbolsLoaded | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77e28b608d5c0db1d26d83f2d9a5786877a3ba73
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635121"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Uygulama etki alanı tanımlayıcısı verilen belirtilen modül için hata ayıklama simgelerinin yüklenip yüklenmediğini belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
'ndaki Uygulama etki alanı için tanımlayıcı.

`guidModule`\
'ndaki Modül için benzersiz tanımlayıcı.

## <a name="return-value"></a>Dönüş Değeri
Hata ayıklama sembolleri yüklüyse, öğesini döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` .

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
