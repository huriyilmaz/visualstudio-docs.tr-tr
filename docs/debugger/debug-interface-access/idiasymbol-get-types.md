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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9258e80ea3a3a050daebc1ea1189a573733c928b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074399"
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
