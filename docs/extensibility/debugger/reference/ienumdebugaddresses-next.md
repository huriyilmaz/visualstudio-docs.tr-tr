---
title: IEnumDebugAdresleri::Sonraki | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88deefddc5b479d7173c4de1c574c4da92631e97
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717644"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Bu yöntem, numaralandırmadan sonraki eleman kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Alınacak öğe sayısı. Ayrıca `rgelt` dizinin en büyük boyutunu belirtir.

`rgelt`\
[içinde, dışarı] Doldurulacak [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) öğeleri dizisi.

`pceltFetched`\
[çıkış] Gerçekte döndürülen öğe sayısını `rgelt`döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. İstenen öğe sayısından daha az ise döndürür; `S_FALSE` aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
