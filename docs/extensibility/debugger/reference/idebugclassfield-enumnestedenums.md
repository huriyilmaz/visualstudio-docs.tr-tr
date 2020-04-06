---
title: IDebugClassField::EnumNestedEnums | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734412"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Bu sınıfın iç içe geçen sayısalatörleri için bir sayısallaştırıcı oluşturur.

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
[çıkış] İç içe geçmelistesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. İç içe geçme ler yoksa null değeri verir.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, iç içe geçme sayısı yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Numaralandırmanın her öğesi iç içe geçen numaralandırmayı açıklayan bir [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) nesnesidir.

Bir sınıf içinde bildirilen numaralandırma iç içe numaralandırma olarak kabul edilir. Örneğin, verilen:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Yöntem, `EnumNestedEnums` numaralandırmayı temsil eden bir [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) nesnesi içeren `NestedEnum` bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
