---
description: Bir numaralama dizisinde belirtilen sayıda segmenti atlar.
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22479a35faf797969eb7936c6d630e91f7f6352b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630117"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Bir numaralama dizisinde belirtilen sayıda segmenti atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Atlama sırasına göre numaralama dizisinde yer alan segmentlerin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK` döndürür; aksi takdirde, `S_FALSE` atlanabilecek başka kesim yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
