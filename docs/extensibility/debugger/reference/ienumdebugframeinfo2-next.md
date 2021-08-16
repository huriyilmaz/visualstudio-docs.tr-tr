---
description: FRAMEINFO enumerasyonundan sonraki öğe kümesi döndürür.
title: IEnumDebugFrameInfo2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42964fde86e4ef68371da014f97be67a2c1b39328bb9dcd5ab94235198aaca6c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377527"
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Numaralamadan sonraki öğe kümesi döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG       celt,
   FRAMEINFO** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   FRAMEINFO[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[in] Alınarak alınan öğe sayısı. Ayrıca dizinin en büyük boyutunu `rgelt` belirtir.

`rgelt`\
[in, out] Doldurulması [gereken FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) öğeleri dizisi.

`pceltFetched`\
[out] içinde gerçekten döndürülen öğe sayısını `rgelt` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. İstenen `S_FALSE` sayıdan daha az öğe döndürüleninse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
