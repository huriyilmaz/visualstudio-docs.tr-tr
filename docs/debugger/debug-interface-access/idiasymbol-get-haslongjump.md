---
description: İşlevin longjmp) komutunun bir kullanımını içerip içermediğini belirten bir bayrak alır (bir setjmp (/CPP/c-Runtime-Library/Reference/setjmp) komutuyla eşleştirilmiş, bu, özel durum işlemenin C stili yöntemini oluşturur).
title: 'IDiaSymbol:: get_hasLongJump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8de8dcc40d65425540f701b6b833da234b800bf5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628058"
---
# <a name="idiasymbolget_haslongjump"></a>IDiaSymbol::get_hasLongJump
İşlevin [longjmp](/cpp/c-runtime-library/reference/longjmp) komutunun bir kullanımını içerip içermediğini belirten bir bayrak alır (bir [setjmp](/cpp/c-runtime-library/reference/setjmp) komutuyla eşleştirilmiş, bu, özel durum işlemenin C stili yöntemini oluşturur).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İşlev bir komut içeriyorsa döndürür `longjmp` ; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)
