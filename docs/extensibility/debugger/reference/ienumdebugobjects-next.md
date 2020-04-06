---
title: IEnumDebugObjects::Sonraki | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99b2bc35b63a4e97f888365f1d11231ae620b69c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716339"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Bu yöntem, numaralandırmadan sonraki eleman kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Alınacak öğe sayısı. Ayrıca `rgelt` dizinin en büyük boyutunu belirtir.

`rgelt`\
[içinde, dışarı] Doldurulacak [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) öğeleri dizisi.

`pceltFetched`\
[çıkış] Gerçekte döndürülen öğe sayısını `rgelt`döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. İstenen öğe sayısından daha az ise döndürür; `S_FALSE` aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
