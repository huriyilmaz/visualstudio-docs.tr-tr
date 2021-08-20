---
description: Bu sınıfın iç içe geçmiş numaralayıcıları için bir numaralayıcı oluşturur.
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ad0f51fa0874cf1068c097d20271a0b81178353
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127447"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Bu sınıfın iç içe geçmiş numaralayıcıları için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[out] İç içe [geçmiş liste listesini temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. İç içe geçmiş bir numaralama yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK veya S_FALSE numaralayıcı yoksa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Numaralamanın her öğesi, iç içe geçmiş bir [numaralamayı açıklayan bir IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) nesnesidir.

Bir sınıfın içinde bildirilen bir numaralama, iç içe geçmiş bir numaralama olarak kabul edilir. Örneğin, verilen:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

yöntemi, `EnumNestedEnums` numaralandırıcıyı temsil eden bir [IDebugEnumField nesnesi içeren bir IEnumDebugFields](../../../extensibility/debugger/reference/idebugenumfield.md) nesnesi [](../../../extensibility/debugger/reference/ienumdebugfields.md) `NestedEnum` dönüşer.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
