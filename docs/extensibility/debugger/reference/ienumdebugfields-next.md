---
title: 'IEnumDebugFields:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 216ce9d49ba9de33307ad692787d6e6d36ee15c3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727658"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
Bu yöntem, Numaralandırmadaki öğelerin bir sonraki kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
'ndaki Alınacak öğe sayısı. Ayrıca `rgelt` dizisinin en büyük boyutunu belirtir.

`rgelt`\
[in, out] Doldurulacak [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) öğelerinin dizisi.

`pceltFetched`\
dışı @No__t_0 ' de gerçekten döndürülen öğe sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. İstenen sayıda öğeden daha az döndürülürse `S_FALSE` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)