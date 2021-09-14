---
description: Numaralama dizisinde belirtilen sayıda tablo alma.
title: IDiaEnumTables::Next | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 77a8f8a6e933d8655085d5c9e4537391ecf6c7e9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629931"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Numaralama dizisinde belirtilen sayıda tablo alma.

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

[in] Numaralayıcıdaki alınarak alınan tablo sayısı.

 `rgelt`

[out] İstenen tabloları temsil eden [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesneleriyle doldurulması gereken bir dizi.

 `pceltFetched`

[out] Getirili numaralayıcıdaki tablo sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` tablo yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
