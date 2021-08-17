---
description: Bu genel parametreyle ilişkili kısıtlamaların sayısını döndürür.
title: 'Idebuggenericparamfield:: ConstraintCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f49b98fe463977790230201a146a79375f005321aa353d9a2a59e9ac6dd7296
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292448"
---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
Bu genel parametreyle ilişkili kısıtlamaların sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ConstraintCount(
    ULONG32* pcConst
);
```

```csharp
int ConstraintCount(
    ref uint pcConst
);
```

## <a name="parameters"></a>Parametreler
`pcConst`\
[in, out] Bu alanla ilişkili kısıtlamaların sayısı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [ıdebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) arabirimini kullanıma sunan bir **cdebuggenericparamtcobject** için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );

    IfFalseGo(pcConst, E_INVALIDARG );
    *pcConst = 0;
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              NULL,
              0,
              &cConst) );
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    *pcConst = cConst;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
