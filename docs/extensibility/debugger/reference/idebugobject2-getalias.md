---
description: Varsa, bu nesneyle ilişkili diğer adı alır.
title: 'IDebugObject2:: GetAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2cbf4a84af4001519617a7e6306c4139e763aea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053795"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Varsa, bu nesneyle ilişkili diğer adı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`ppAlias`\
dışı Bu nesne için diğer adı temsil eden bir [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) nesnesi döndürür; Aksi takdirde, null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir nesne için bir diğer ad [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) yöntemi çağrısıyla oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
