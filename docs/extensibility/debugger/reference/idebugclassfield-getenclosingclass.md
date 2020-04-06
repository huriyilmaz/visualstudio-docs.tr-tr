---
title: IDebugClassField::GetEnclosingClass | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734398"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Bu sınıfı içine alan sınıfı alır.

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
[çıkış] Çevreleyen sınıfı temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür. Çevreleyen sınıf yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi tarafından temsil edilen sınıf iç `ppClassField` içe bir `IDebugClassField` sınıfsa, parametre çevreleyen sınıfı temsil eden bir nesne döndürür. Örneğin, bu sınıf tanımı göz önüne alındığında:

```
class RootClass {
    class NestedClass { }
};
```

`NestedClass` Sınıfı `GetEnclosingClass` temsil eden `IDebugClassField` nesneüzerinde yöntem çağrı `IDebugClassField` sınıfı temsil `RootClass`eden bir nesne döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
