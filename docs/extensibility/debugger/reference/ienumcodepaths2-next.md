---
title: IEnumCodePaths2::Sonraki | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e126fc916360d0cc992da5f17edecda7cb2ef41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717814"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
Numaralandırmadan sonraki eleman kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG       celt,
   CODE_PATH** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   CODE_PATH[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Alınacak öğe sayısı. Ayrıca `rgelt` dizinin en büyük boyutunu belirtir.

`rgelt`\
[içinde, dışarı] Doldurulacak [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) öğeleri dizisi.

`pceltFetched`\
[çıkış] Gerçekte döndürülen öğe sayısını `rgelt`döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. İstenen öğe sayısından daha az ise döndürür; `S_FALSE` aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)
