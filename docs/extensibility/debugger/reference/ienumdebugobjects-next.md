---
description: Bu yöntem, numaralandırmadan sonraki IDebugObject öğelerini döndürür.
title: IEnumDebugObjects::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e126941a3519891a69692fd218ebefc7238be30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095354"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Bu yöntem, numaralamadan sonraki öğe kümesi döndürür.

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
[in] Alınarak alınan öğe sayısı. Ayrıca dizinin en büyük boyutunu `rgelt` belirtir.

`rgelt`\
[in, out] Doldurulması [gereken IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) öğelerinin dizisi.

`pceltFetched`\
[out] içinde gerçekten döndürülen öğe sayısını `rgelt` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. İstenen `S_FALSE` sayıdan daha az öğe döndürüleninse döndürür, aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
