---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743734"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Sabit Listesi dizisinde belirtilen sayıda tabloyu alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 `celt`

'ndaki Numaralandırıcıda alınacak olan tablo sayısı.

 `rgelt`

dışı İstenen tabloları temsil eden [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesneleriyle doldurulacak bir dizi.

 `pceltFetched`

dışı Getirilen Numaralandırıcı içindeki tablo sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür. Daha fazla tablo yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)