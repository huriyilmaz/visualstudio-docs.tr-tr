---
description: Hata ayıklama altyapısının adres alanı içinde yönetilen nesnenin bir kopyasını oluşturur.
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3aa4089a22988bc6a64ca8928dfd7a2b24e300438337ee8646634a4d34b2ae4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307264"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Hata ayıklama altyapısının adres alanı içinde yönetilen nesnenin bir kopyasını oluşturur.

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
[out] Yeni oluşturulan [yönetilen nesneyi temsil eden bir IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür. Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) E_FAIL bir yönetilen değer sınıfı örneğini temsil etmiyorsa, bu değeri döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi, örnek gibi bir yönetilen değer sınıfı örneğini temsil `System.Decimal` eder. Yerel bir kopyaya sahip olarak Evaluate [çağrısının ek](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) yükü ortadan kalkmış olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
