---
title: IEnumDebugReferenceInfo2::Atla | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Skip
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Skip
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2c2247b30d1f300992ef86f80fe44e8ea680fc15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715283"
---
# <a name="ienumdebugreferenceinfo2skip"></a>IEnumDebugReferenceInfo2::Skip
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
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
