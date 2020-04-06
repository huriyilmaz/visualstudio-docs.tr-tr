---
title: IEnumDebugBoundBreakpoints2::Atla | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Skip
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29d96686559218fcdfafda966b708841e1b0fbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717474"
---
# <a name="ienumdebugboundbreakpoints2skip"></a>IEnumDebugBoundBreakpoints2::Skip
Belirtilen öğe sayısını atlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Atlasılayacak öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. Kalan `S_FALSE` `celt` öğelerin sayısından büyükse döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan `celt` öğelerin sayısından daha büyük bir değer belirtirse, numaralandırma sonuna `S_FALSE` ayarlanır ve döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
