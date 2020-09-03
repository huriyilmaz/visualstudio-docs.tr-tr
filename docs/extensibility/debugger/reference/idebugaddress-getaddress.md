---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736612"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Bir nesneyi ve onun kapsam veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.

## <a name="syntax"></a>Söz dizimi

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
