---
description: Hata ayıklama altyapısının adres alanında yönetilen nesnenin bir kopyasını oluşturur.
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56961930e08e7d53dfe387c00642ae7266c230c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081925"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Hata ayıklama altyapısının adres alanında yönetilen nesnenin bir kopyasını oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`ppObject`\
dışı Yeni oluşturulan yönetilen nesneyi temsil eden bir [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür. Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) bir yönetilen değer sınıfı örneğini temsil etmediği E_FAIL döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi, örnek gibi bir yönetilen değer sınıfı örneğini temsil etmelidir `System.Decimal` . Yerel bir kopyaya sahip olarak, [değerlendir](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) çağırma yükü ortadan kalkar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
