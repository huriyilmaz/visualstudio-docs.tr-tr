---
description: Parametre olarak sunulan değer sınıfının örneğinden değer sınıfı nesnesinin örneğinin değerini ayarlar.
title: 'IDebugManagedObject:: SetFromManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b4038b4f3560b7cd526261f898c01f384421f42
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165233"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Parametre olarak sunulan değer sınıfının örneğinden değer sınıfı nesnesinin örneğinin değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parametreler
`pManagedObject`\
'ndaki Yeni değeri içeren yönetilen nesneyi temsil eden bir arabirim.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yönetilen nesneyi [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) nesnesi tarafından temsil edildiği şekilde değiştirmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
