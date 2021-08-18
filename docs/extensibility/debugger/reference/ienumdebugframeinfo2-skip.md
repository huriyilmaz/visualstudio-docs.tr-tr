---
description: Belirtilen sayıda FRAMEINFO öğelerini atlar.
title: IEnumDebugFrameInfo2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Skip
helpviewer_keywords:
- IEnumDebugFrameInfo2::Skip
ms.assetid: 68cd3948-022a-41ad-bd9f-9ab776cf6248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d56b1da6a98f35b112c3397feab79b4a1e79ac51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152828"
---
# <a name="ienumdebugframeinfo2skip"></a>IEnumDebugFrameInfo2::Skip
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
[in] Atlana öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. kalan `S_FALSE` `celt` öğe sayısından büyükse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan öğe sayısından büyük bir değer belirtirse, en sona ayarlanır `celt` ve `S_FALSE` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
