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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22b5f3a98afa2be496295dd13e8ec1c2b5f08a1b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034987"
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
