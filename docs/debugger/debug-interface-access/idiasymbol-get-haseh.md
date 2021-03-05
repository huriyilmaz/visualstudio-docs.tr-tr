---
description: İşlevin yönetilmeyen C++ stili özel durum işleme (örneğin, bir try/catch bloğu) içerip içermediğini belirten bir bayrak alır.
title: 'IDiaSymbol:: get_hasEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d60a47c4d655bd0a489d293c88ea5b318971547d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156309"
---
# <a name="idiasymbolget_haseh"></a>IDiaSymbol::get_hasEH
İşlevin yönetilmeyen C++ stili özel durum işleme (örneğin, bir try/catch bloğu) içerip içermediğini belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İşlevin herhangi bir C++ stili özel durum işleme sahip olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .

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
