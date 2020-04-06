---
title: IDebugObject::IsEqual | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726507"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Bir nesneyi bu nesneyle karşılaştırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parametreler
`pObject`\
[içinde] Karşılaştırılması gereken nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi.

`pfIsEqual`\
[çıkış] Nesnelerin değerleri eşitse sıfır olmayan (`TRUE`) döndürür; aksi takdirde,`FALSE`sıfır () döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genellikle, bu yöntem `pObject` parametre ve bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi tarafından temsil edilen değerlerin adreslerini karşılaştırabilirsiniz; adresler eşitse, nesneler eşit kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
