---
description: İş parçacığı numaralamada belirtilen öğe sayısını atlar.
title: IEnumDebugThreads2::| Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Skip
helpviewer_keywords:
- IEnumDebugThreads2::Skip
ms.assetid: eab068d4-1f8d-44cd-bc54-92a10fe23de6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1483bb2139cb5d2bdfa0a9a619d494bd52fa627
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636238"
---
# <a name="ienumdebugthreads2skip"></a>IEnumDebugThreads2::Skip
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
[in] Atlan öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. kalan `S_FALSE` `celt` öğe sayısından büyükse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan öğe sayısından büyük bir değer belirtirse, en sona ayarlanır `celt` ve `S_FALSE` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
