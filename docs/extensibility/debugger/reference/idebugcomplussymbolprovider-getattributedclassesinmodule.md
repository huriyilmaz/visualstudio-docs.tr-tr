---
description: Belirli bir modülde belirtilen özniteliğe sahip sınıfları alır.
title: IDebugComPlusSymbolProvider::GetAttributedClassesinModule
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAttributedClassesinModule
- GetAttributedClassesinModule
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6c6a72f6c7135882ece0b311478fe1f6f048a6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635070"
---
# <a name="idebugcomplussymbolprovidergetattributedclassesinmodule"></a>IDebugComPlusSymbolProvider::GetAttributedClassesinModule
Belirli bir modülde belirtilen özniteliğe sahip sınıfları alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAttributedClassesinModule (
    ULONG32            ulAppDomainID,
    GUID               guidModule,
    LPOLESTR           pstrAttribute,
    IEnumDebugFields** ppEnum
);
```

```csharp
int GetAttributedClassesinModule (
    uint                 ulAppDomainID,
    Guid                 guidModule,
    string               pstrAttribute,
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
'ndaki Uygulama etki alanının tanımlayıcısı.

`guidModule`\
'ndaki Modülün benzersiz tanıtıcısı.

`pstrAttribute`\
'ndaki Öznitelik dizesi.

`ppEnum`\
dışı Öznitelikli sınıfların bir listesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    __in_z LPOLESTR pstrAttribute,
    IEnumDebugFields** ppEnum
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    CComPtr<IMetaDataImport> pMetaData;
    Module_ID idModule(ulAppDomainID, guidModule);
    const void* pUnused;
    ULONG cbUnused;
    HCORENUM hEnum = 0;
    ULONG cTypeDefs = 0;
    ULONG cEnum;
    DWORD iTypeDef = 0;
    mdTypeDef* rgTypeDefs = NULL;
    IDebugField** rgFields = NULL;
    DWORD ctField = 0;
    CEnumDebugFields* pEnumFields = NULL;

    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );

    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );
    IfFailGo( GetModule( idModule, &pModule ) );
    pModule->GetMetaData( &pMetaData );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       NULL,
                                       0,
                                       &cTypeDefs ) );

    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );
    pMetaData->CloseEnum(hEnum);
    hEnum = NULL;

    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       rgTypeDefs,
                                       cEnum,
                                       &cTypeDefs ) );

    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)
    {

        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],
                pstrAttribute,
                &pUnused,
                &cbUnused ) == S_OK)
        {
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)
            {
                ctField++;
            }
            else
            {
                ASSERT(!"Failed to Create Attributed Class");
            }
        }
    }

    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),
                                           (void**) ppEnum ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );

    DELETERG( rgTypeDefs );

    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)
    {
        RELEASE( rgFields[iTypeDef] );
    }

    DELETERG( rgFields );
    RELEASE( pEnumFields );

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
