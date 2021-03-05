---
description: Sabit Listesi dizisinde belirtilen sayıda tabloyu alır.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc207633a083e841221e3c6ca527c7ffb3dbcf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157884"
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
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla tablo yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
