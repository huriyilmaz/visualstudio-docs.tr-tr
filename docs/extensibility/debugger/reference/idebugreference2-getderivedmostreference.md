---
description: Bir başvurudan türetilmiş en çok başvuru alır.
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2980792572a6ac9c2d833a0fef62350db968d00
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725154"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Bir başvurudan türetilmiş en çok başvuru alır. Daha sonraki kullanımlar için ayrılmıştır.

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
[out] Türetilmiş en [çok özelliği temsil eden bir IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bu özellik uygulayan ancak aslında 'den türetilen bir örneği olan bir nesneyi açıklarsa, bu yöntem nesnesine bir başvuruyu temsil eden `ClassRoot` `ClassDerived` bir `ClassRoot` [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi `ClassDerived` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
