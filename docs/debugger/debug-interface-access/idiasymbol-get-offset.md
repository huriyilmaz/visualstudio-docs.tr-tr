---
title: 'IDiaSymbol:: get_Offset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: feb7620e507c5e57cf025211e42d541440af22f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739583"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
Sembol konumunun sapmasını alır. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` veya `LocIsBitField` olduğunda kullanın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Sembol konumunun bayt cinsinden sapmasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu fark, daha önce belirlenen bilinen bir noktadan. Örneğin, `LocIsBitField` bir konum türünün konumu genellikle kapsayan sınıfın başından itibaren oluşur.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)