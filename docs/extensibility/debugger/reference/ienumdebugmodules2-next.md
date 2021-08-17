---
description: Modüller numaralamadan sonraki öğe kümesi döndürür.
title: IEnumDebugModules2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c82868895f41e8af5849b53310ccf1d5c65cd96df2711b82607a8be39fcb573
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389130"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Numaralamadan sonraki öğe kümesi döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[in] Alınarak alınan öğe sayısı. Ayrıca dizinin en büyük boyutunu `rgelt` belirtir.

`rgelt`\
[in, out] Doldurulması [gereken IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) öğelerinin dizisi.

`pceltFetched`\
[out] içinde gerçekten döndürülen öğe sayısını `rgelt` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. İstenen `S_FALSE` sayıdan daha az öğe döndürüleninse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
