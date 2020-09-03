---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727704"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Parametre olarak sunulan değer sınıfının örneğinden değer sınıfı nesnesinin örneğinin değerini ayarlar.

## <a name="syntax"></a>Söz dizimi

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
