---
title: IDebugObject::GetManagedDebugObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726683"
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
[çıkış] Yeni oluşturulan yönetilen nesneyi temsil eden bir [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür. Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) yönetilen bir değer sınıfı örneğini temsil etmiyorsa E_FAIL döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu [Hata Ayıknesne](../../../extensibility/debugger/reference/idebugobject.md) nesnesi, örnek `System.Decimal` gibi yönetilen bir değer sınıfı örneğini temsil etmelidir. Yerel bir kopyaya sahip olarak, [Değerlendir'i](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) aramanın genel gideri ortadan kalkar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
