---
description: Bir nesneyi bu nesneyle karşılaştırır.
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151668"
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
'ndaki Karşılaştırılacak nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi.

`pfIsEqual`\
dışı `TRUE`Nesnelerin değerleri eşitse sıfır olmayan () döndürür; Aksi takdirde, sıfır ( `FALSE` ) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genellikle, bu yöntem, parametresiyle temsil edilen değerlerin adreslerini `pObject` ve bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesini karşılaştırabilir; adresler eşitse, nesneler eşit kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
