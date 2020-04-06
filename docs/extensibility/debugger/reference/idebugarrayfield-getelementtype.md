---
title: IDebugArrayField::GetElementType | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3870f28ffb62239d0a092093d28c83d25e92bd31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736337"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Dizideki öğe türünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametreler
`ppType`\
[çıkış] Öğe türünü açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) nesnesi, dizinin tüm öğelerinin aynı türde olduğunu varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
