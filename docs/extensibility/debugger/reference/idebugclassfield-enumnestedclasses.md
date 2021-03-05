---
description: Bu sınıfta iç içe yerleştirilmiş sınıflar için bir Numaralandırıcı oluşturur.
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87538db39df590fd3885f545e5442c7dafecb9a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164272"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Bu sınıfta iç içe yerleştirilmiş sınıflar için bir Numaralandırıcı oluşturur.

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
dışı İç içe sınıfların listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. İç içe geçmiş sınıflar yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, iç içe sınıf yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Sabit listesinin her öğesi, iç içe bir sınıfı tanımlayan bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesidir.

İç içe yerleştirilmiş bir sınıf, başka bir sınıfın içinde tanımlanan bir sınıftır. Örnek:

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) numaralandırması, sınıfı temsil eden bir nesne içerir `NestedClass` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
