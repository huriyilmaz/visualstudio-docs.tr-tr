---
description: Bir özelliğin türetilmiş en fazla özelliğini alır.
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d202ba8594031cb72da1306e0828ef32423ac55c8cacfb58247ac6d373896b6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402499"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Bir özelliğin türetilmiş en fazla özelliğini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametreler
`ppDerivedMost`\
[out] Türetilmiş en [çok özelliği temsil eden bir IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür. Almak `S_GETDERIVEDMOST_NO_DERIVED_MOST` için türetilmiş en çok özelliği yoksa döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bu özellik uygulayan ancak aslında 'den türetilen bir örneği olan bir nesneyi açıklarsa, bu yöntem nesneyi `ClassRoot` `ClassDerived` açıklayan bir `ClassRoot` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi `ClassDerived` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
