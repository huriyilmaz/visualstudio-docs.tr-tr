---
description: Bu genel parametrenin bayraklarını alır.
title: 'Idebuggenericparamfield:: GetFlags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8dc6360819c1a8ec49a58896a2042d35884ed4a0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063311"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Bu genel parametrenin bayraklarını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

## <a name="parameters"></a>Parametreler
`pdwFlags`\
dışı Bu genel parametrenin bayraklarını döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar çeşitli özel kısıtlamalar hakkında bilgi içerir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [ıdebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) arabirimini kullanıma sunan bir **cdebuggenericparamtcobject** için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
