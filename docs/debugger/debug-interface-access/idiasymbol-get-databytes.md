---
description: Bir OEM sembolünün veri baytlarını alır.
title: 'IDiaSymbol:: get_dataBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fbf794feee79ae8865165c31cc5dfc7c07730b55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036186"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
Bir OEM sembolünün veri baytlarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 `cbData`

'ndaki Verilerin tutulacağı arabelleğin boyutu.

 `pcbData`

dışı Yazılan bayt sayısını döndürür veya `data` parametresi ise, `NULL` kullanılabilir bayt sayısını döndürür.

 `data[]`
- [Out,] Veri baytları ile doldurulmuş bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
