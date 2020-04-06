---
title: IDebugObject2::GetAlias | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726279"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Varsa, bu nesneyle ilişkili diğer adı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`ppAlias`\
[çıkış] Bu nesnenin diğer adını temsil eden bir [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) nesnesi döndürür; aksi takdirde, null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) yöntemine yapılan çağrıyla nesnenin diğer adı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
