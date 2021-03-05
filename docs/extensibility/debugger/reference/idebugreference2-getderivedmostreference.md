---
description: Bir başvurunun türetilmiş en çok başvurusunu alır.
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1517b1be34b62defcd5f19792baa2ac6c343b85b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168982"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Bir başvurunun türetilmiş en çok başvurusunu alır. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametreler
`ppDerivedMost`\
dışı En çok türetilen özelliği temsil eden bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bu özellik, `ClassRoot` tarafından türetilen ancak gerçekten bir örnek oluşturma olan bir nesne tanımlıyor `ClassDerived` `ClassRoot` , bu yöntem, nesne başvurusunu temsil eden bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi döndürür `ClassDerived` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
