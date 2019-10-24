---
title: 'IDiaEnumSegments:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744197"
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
 Başarılı olursa `S_OK`döndürür. Daha fazla kesim yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)