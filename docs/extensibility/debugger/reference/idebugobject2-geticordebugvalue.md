---
description: Bu nesneyle ilişkili değeri temsil eden bir yönetilen kod nesnesi alır.
title: 'IDebugObject2:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b25d5147283ad14b77e216a23a45f69516951908
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053756"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Bu nesneyle ilişkili değeri temsil eden bir yönetilen kod nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametreler
`ppUnk`\
[out] `IUnknown` Bu diğer adı temsil eden arabirim. Bu arabirim arabirim için sorgulanabilir `ICorDebugValue` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `ICorDebugValue`Nesnesi, bir değeri temsil eden ortak bir dil çalışma zamanı arabirimidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
