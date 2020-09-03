---
title: 'IDiaSymbol:: get_bitPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_bitPosition method
ms.assetid: b0059407-8655-497b-81ca-025595989371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 636f553d72dc73f463d7b9814230f4b80cdda535
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464172"
---
# <a name="idiasymbolget_bitposition"></a>IDiaSymbol::get_bitPosition
Konumun bit konumunu alır. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olduğunda kullanılır `LocIsBitField` .

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_bitPosition ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Konumun bit konumunu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Description|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)