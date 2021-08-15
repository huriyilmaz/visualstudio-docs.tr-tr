---
description: Bu simge için derleyiciye özgü türlerden bir diziyi döndürür.
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e0dacb8d9fa997c3509015d1824d88ebf152863c461fad299906a235d4541f16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391619"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Bu simge için derleyiciye özgü türlerden bir diziyi döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parametreler
 `cTypes`

[in] Verileri tutmak için arabelleğin boyutu.

 `pcTypes`

[out] Yazılan türlerin sayısını veya parametresi ise `types` kullanılabilir toplam tür sayısını `NULL` döndürür.

 `types[]`

[out] Bu simgenin tüm türlerini temsil eden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesneleriyle doldurulacak bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
