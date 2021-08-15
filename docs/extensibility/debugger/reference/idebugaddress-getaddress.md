---
description: Bir nesneyi ve nesnesinin kapsamını veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7cfdadd5a2acb31525e0329f485ac289a8ecc4c888a1ff73ca7accaea736574
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239236"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Bir nesneyi ve nesnesinin kapsamını veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.

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
[in, out] Bu [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) doldurulan bir yapıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 DEBUG_ADDRESS [](../../../extensibility/debugger/reference/debug-address.md) yapısı bu yönteme geçirildi ve ardından uygun bilgilerle doldurulacak. Bu bilgilerin nasıl yorumlanması döndürülen bilgi türüne ve sembol işleyicinin kendisine bağlıdır. Diğer [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) için bkz.

## <a name="see-also"></a>Ayrıca bkz.
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
