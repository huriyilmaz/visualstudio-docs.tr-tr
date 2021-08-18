---
description: Bu sınıfta iç içe geçmiş sınıflar için bir numaralayıcı oluşturur.
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1b31e31df47dd2668f175f0dc1960bb272e23fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119717"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Bu sınıfta iç içe geçmiş sınıflar için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[out] İç içe geçmiş sınıflar listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. İç içe geçmiş sınıf yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK veya S_FALSE sınıf yoksa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Numaralamanın her öğesi, iç içe geçmiş bir sınıfı açıklayan [bir IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesidir.

İç içe geçmiş bir sınıf, başka bir sınıfın içinde tanımlanan bir sınıftır. Örnek:

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumeration sınıfı temsil eden bir nesne `NestedClass` içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
