---
description: Bu genel parametrenin türünü veya yöntem sahibini alın.
title: IDebugGenericParamField::GetOwner | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetOwner
ms.assetid: c7f6d166-a69e-40c4-bd0b-1a1fdf9aaacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ae75c99d8ffe1ed2b6206ff5128e3f4f1ae293d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064132"
---
# <a name="idebuggenericparamfieldgetowner"></a>IDebugGenericParamField::GetOwner
Bu genel parametrenin türünü veya yöntem sahibini alın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetOwner(
    IDebugField** ppOwner
);
```

```csharp
int GetOwner(
    out IDebugField ppOwner
);
```

## <a name="parameters"></a>Parametreler
`ppOwner`\
[out] Bu genel [parametreye sahip olan IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, **IDebugGenericParamField arabirimini ortaya çıkaran bir CDebugGenericParamFieldType** nesnesi için bu yöntemin nasıl [uygulandığını](../../../extensibility/debugger/reference/idebuggenericparamfield.md) gösterir.

```cpp
HRESULT CDebugGenericParamFieldType::GetOwner(IDebugField** ppOwner)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetOwner );

    IfFalseGo(ppOwner, E_INVALIDARG );
    *ppOwner = NULL;

    IfFailGo( this->LoadProps() );
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );

    switch (TypeFromToken(m_tokOwner))
    {
        case mdtMethodDef:
            {
                mdTypeDef tokClass;
                CComPtr<IDebugField> pClass;
                CDEBUG_ADDRESS caddr;
                CComPtr<IDebugContainerField> pContainer;

                IfFailGo( pMetadata->GetMethodProps( m_tokOwner, &tokClass, NULL, 0, NULL, NULL, NULL, NULL, NULL, NULL ) );
                IfFailGo( m_spSH->CreateClassType(m_idModule, tokClass, &pClass) );
                IfFailGo( pClass->QueryInterface( &pContainer ) );
                IfFailGo( caddr.InitializeMethod( m_idModule, tokClass, m_tokOwner, 0, 0 ) );
                IfFailGo( m_spSH->CreateMethodSymbol( pContainer, caddr, FIELD_SYM_MEMBER, ppOwner ) );
                break;
            }
        case mdtTypeDef:
            {
                IfFailGo( m_spSH->CreateClassType(m_idModule, m_tokOwner, ppOwner) );
                break;
            }
        default:
            {
                ASSERT(!"Unexpected Owner type for Generic Param Field");
                hr = E_FAIL;
            }
    }
Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetOwner, hr );
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
