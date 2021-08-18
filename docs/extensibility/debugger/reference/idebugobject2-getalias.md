---
description: Varsa, bu nesneyle ilişkili diğer adı alır.
title: IDebugObject2::GetAlias | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 494f76bc57ad75a8a52a7b8ce02ed3cb26861be591553e0b406ffe977695f65a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416995"
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
[out] Bu nesnenin diğer adını temsil eden bir [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) nesnesi döndürür; aksi takdirde, bir null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) yöntemine yapılan çağrıyla bir nesnenin diğer adı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
