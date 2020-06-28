---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 9d425e16e18338c0269ccbf88030a47c7b184507
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467528"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Sabit Listesi dizisinde belirtilen sayıda tabloyu alır.

## <a name="syntax"></a>Söz dizimi

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
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla tablo yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)