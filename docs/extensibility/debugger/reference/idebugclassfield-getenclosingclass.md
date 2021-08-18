---
description: Bu sınıfı kapsayan sınıfı alır.
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd6f6314afd1489609d5f93a44f3645cb70de8e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072422"
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
[out] Kapsayan sınıfı [temsil eden bir IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür. Kapsayan bir sınıf yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi tarafından temsil edilen sınıf iç içe geçmiş bir sınıfsa, parametre kapsayan sınıfı temsil eden `ppClassField` bir nesne `IDebugClassField` döndürür. Örneğin, bu sınıf tanımına göre:

```
class RootClass {
    class NestedClass { }
};
```

sınıfını `GetEnclosingClass` temsil eden `IDebugClassField` nesnede yöntemini `NestedClass` çağırma, `IDebugClassField` sınıfını temsil eden bir nesne `RootClass` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
