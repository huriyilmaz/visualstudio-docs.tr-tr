---
description: Program enumerasyonundan sonraki öğe kümesi döndürür.
title: IEnumDebugPrograms2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e1709d8b55224fc4eb221cd65766f6d70fb3ccf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725107"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
Numaralamadan sonraki öğe kümesi döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[in] Alınarak alınan öğe sayısı. Ayrıca dizinin en büyük boyutunu `rgelt` belirtir.

`rgelt`\
[in, out] Doldurulması [gereken IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) öğeleri dizisi.

`pceltFetched`\
[out] içinde gerçekten döndürülen öğe sayısını `rgelt` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. İstenen `S_FALSE` sayıdan daha az öğe döndürüleninse döndürür, aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
