---
description: İşlevin longjmp) komutunun kullanımını (setjmp(/cpp/c-runtime-library/reference/setjmp) komutuyla eşleştirilmiş olup olmadığını belirten bir bayrak alır, bunlar özel durum işlemenin C stili yöntemini oluşturur).
title: IDiaSymbol::get_hasLongJump | Microsoft Docs
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121524"
---
# <a name="idiasymbolget_haslongjump"></a>IDiaSymbol::get_hasLongJump
İşlevin [longjmp](/cpp/c-runtime-library/reference/longjmp) komutunun kullanımının olup olmadığını belirten bir bayrak alır [(setjmp](/cpp/c-runtime-library/reference/setjmp) komutuyla eşleştirilmiştir, bunlar özel durum işlemenin C stili yöntemini oluşturur).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] İşlev `TRUE` bir komut içeriyorsa `longjmp` döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)
