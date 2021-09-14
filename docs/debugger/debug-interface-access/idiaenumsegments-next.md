---
description: Numaralama dizisinde belirtilen sayıda segmenti alan.
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5aaed8e83a49ab31844d7fddd5f8e036fdc0d6cd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630135"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Numaralama dizisinde belirtilen sayıda segmenti alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıda alınan segmentlerin sayısı.

 Rgelt

[out] Segmentleri temsil eden istenen [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesneleriyle doldurulması gereken bir dizi.

 pceltFetched

[out] Getirili numaralayıcıda segment sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` segment yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
