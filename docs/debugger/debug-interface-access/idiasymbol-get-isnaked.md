---
description: İşlevin çıplak) özniteliğine sahip olup olmadığını belirten bir bayrak alır (başka bir ifadeyle, işlevin derleyici tarafından eklenen giriş veya son giriş kodu yoktur).
title: IDiaSymbol::get_isNaked | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c1bc54c29a94c79be4dafae45128ddb63595f45aec489da7e4e3a0c59a71b45e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436422"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
İşlevin çıplak özniteliğine sahip olup [](/cpp/cpp/naked-cpp) olmadığını belirten bir bayrak alır (diğer bir ifade, işlevin derleyici tarafından eklenen giriş veya son giriş kodu yoktur).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] işlevi `TRUE` özniteliğine sahipse `naked` döndürür; aksi takdirde `FALSE` döndürür.

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
- [Naked İşlev Çağrıları](/cpp/cpp/naked-function-calls)
