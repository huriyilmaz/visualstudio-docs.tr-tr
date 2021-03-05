---
description: İşlevin setjmp) komutunun bir kullanımını içerip içermediğini belirten bir bayrak alır (longjmp (/CPP/c-Runtime-Library/Reference/longjmp) komutuyla eşleştirilmiş, bu, özel durum işlemenin C stili yöntemini oluşturur).
title: 'IDiaSymbol:: get_hasSetJump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b0721969fb9419c8467fdd6019ff4de5aaf761c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160927"
---
# <a name="idiasymbolget_hassetjump"></a>IDiaSymbol::get_hasSetJump
İşlevin [setjmp](/cpp/c-runtime-library/reference/setjmp) komutunun bir kullanımını içerip içermediğini belirten bir bayrak alır (Bu, [longjmp](/cpp/c-runtime-library/reference/longjmp) komutuyla eşleştirilmiş, bu, özel durum işlemenin C stili yöntemini oluşturur).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasSetJump(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İşlev bir komut içeriyorsa döndürür `setjmp` ; Aksi takdirde, döndürür `FALSE` .

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
- [IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)
