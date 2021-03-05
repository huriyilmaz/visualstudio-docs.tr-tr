---
description: Bir nesneyi ve onun kapsam veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c52d12d8c357f4dbadeef673a3dc4474713ce9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145449"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Bir nesneyi ve onun kapsam veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
[in, out] Bu yöntem tarafından doldurulan bir [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısı bu yönteme geçirilir ve ardından bunu ilgili bilgilerle doldurur. Bu bilgilerin nasıl yorumlanacağı, döndürülen bilgi türüne ve sembol işleyicisine bağlıdır. Daha fazla bilgi için bkz. [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Ayrıca bkz.
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
