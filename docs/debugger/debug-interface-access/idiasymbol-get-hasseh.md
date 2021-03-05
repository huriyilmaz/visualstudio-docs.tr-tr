---
description: İşlevin yapılandırılmış özel durum Işleme (C/C++)) içerip içermediğini belirten bir bayrak alır (örneğin, _try/__except blokları).
title: 'IDiaSymbol:: get_hasSEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a802a14c1c4e9b9c3b080c751d8cd512c3adf75d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156268"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
İşlevin [yapılandırılmış özel durum işleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) içerip içermediğini belirten bir bayrak alır (örneğin, __try/ \_ _Except blokları).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İşlevin yapılandırılmış özel durum işleme blokları varsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Yapılandırılmış Özel Durum İşleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)
