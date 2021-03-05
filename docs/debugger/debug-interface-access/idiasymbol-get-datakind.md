---
description: Bir veri sembolünün değişken sınıflandırmasını alır.
title: 'IDiaSymbol:: get_dataKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataKind method
ms.assetid: 45005ad0-8b29-4cde-9d33-6bef72f6e463
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 833ff0fb6602d7f33aabbb9aa1a442bda07a379b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161011"
---
# <a name="idiasymbolget_datakind"></a>IDiaSymbol::get_dataKind
Bir veri sembolünün değişken sınıflandırmasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_dataKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Örneğin, genel, statik veya sabit gibi veri türünü belirten [DataKind sabit](../../debugger/debug-interface-access/datakind.md) listesi numaralandırmasından bir değer döndürür.

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
- [DataKind Numaralandırması](../../debugger/debug-interface-access/datakind.md)
