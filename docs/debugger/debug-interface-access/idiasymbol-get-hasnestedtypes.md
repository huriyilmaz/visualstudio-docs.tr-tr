---
description: Kullanıcı tanımlı veri türünün iç içe geçmiş tür tanımlarına sahip olup olmadığını belirten bir bayrak alır.
title: 'IDiaSymbol:: get_hasNestedTypes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasNestedTypes method
ms.assetid: 1a8306bd-10dd-40a9-81fc-01f71c348484
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52efb012ef713c2308e3fc7b6b28367327e8311
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156288"
---
# <a name="idiasymbolget_hasnestedtypes"></a>IDiaSymbol::get_hasNestedTypes
Kullanıcı tanımlı veri türünün iç içe geçmiş tür tanımlarına sahip olup olmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasNestedTypes ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Kullanıcı tanımlı veri türünün iç içe geçmiş tür tanımlarına sahip olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .

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
