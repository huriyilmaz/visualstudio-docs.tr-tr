---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8e87efa1ed616a38ccb79fec1e286417c10124b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468032"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Sabit Listesi dizisinde belirtilen sayıda segment alır.

## <a name="syntax"></a>Söz dizimi

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