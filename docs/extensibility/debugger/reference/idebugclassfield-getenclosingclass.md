---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91a4e04e26a57247a541c565ea4f0f392a413d39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925051"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Bu sınıfı kapsayan sınıfı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parametreler
`ppClassField`\
dışı Kapsayan sınıfı temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür. Kapsayan sınıf yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi tarafından temsil edilen sınıf iç içe bir sınıf ise, `ppClassField` parametre `IDebugClassField` kapsayan sınıfı temsil eden bir nesne döndürür. Örneğin, bu sınıf tanımı verildiğinde:

```
class RootClass {
    class NestedClass { }
};
```

`GetEnclosingClass` `IDebugClassField` Sınıfını temsil eden nesne üzerinde yöntemi çağırmak, `NestedClass` `IDebugClassField` sınıfını temsil eden bir nesne döndürür `RootClass` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
