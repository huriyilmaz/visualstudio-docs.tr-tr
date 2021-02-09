---
title: 'Idebuggenericparamfield:: GetFlags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be9f842db6b322ffb9bdc76ebd2a954d849e5d65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929829"
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
