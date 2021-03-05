---
description: Bu simge için derleyiciye özgü türlerin dizisini alır.
title: 'IDiaSymbol:: get_types | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: aec5db878c87ba257f1f83458d1ae742272a9b0f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160605"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Bu simge için derleyiciye özgü türlerin dizisini alır.

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

'ndaki Verilerin tutulacağı arabelleğin boyutu.

 `pcTypes`

dışı Yazılan türlerin sayısını veya parametresi ise, `types` `NULL` kullanılabilir toplam tür sayısını döndürür.

 `types[]`

dışı Bu sembolün tüm türlerini temsil eden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesneleriyle doldurulacak bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
