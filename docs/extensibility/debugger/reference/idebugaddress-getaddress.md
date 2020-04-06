---
title: IDebugAddress::GetAddress | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736612"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Nesneyi ve konumunu kapsamı veya kapsayıcısı içinde açıklayan bir yapı döndürür.

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
[içinde, dışarı] Bu yöntemle doldurulan [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) bir yapıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısı bu yönteme aktarılır ve bu yöntem uygun bilgilerle doldurulur. Bu bilgilerin nasıl yorumlanacağı, döndürülen bilginin türüne ve sembol işleyicisinin kendisine bağlıdır. Daha fazla bilgi için [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
