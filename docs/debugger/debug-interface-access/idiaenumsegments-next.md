---
description: Sabit Listesi dizisinde belirtilen sayıda segment alır.
title: 'IDiaEnumSegments:: Next | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 95d4ac6d566033472d7769e4a1a5df86cdf7ff70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159232"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Sabit Listesi dizisinde belirtilen sayıda segment alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınmayacak Numaralandırıcı içindeki parçaların sayısı.

 rgelt

dışı Segmentleri temsil eden istenen [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesneleriyle doldurulacak bir dizi.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki segmentlerin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla kesim yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
