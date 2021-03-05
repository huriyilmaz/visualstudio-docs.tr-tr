---
description: İşlevin bir en fazla dönüş içerip içermediğini belirten bir bayrak alır.
title: 'IDiaSymbol:: get_farReturn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_farReturn method
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bebf0d1f61c6cf1dc21528e44703de049d247c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156344"
---
# <a name="idiasymbolget_farreturn"></a>IDiaSymbol::get_farReturn
İşlevin bir en fazla dönüş içerip içermediğini belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_farReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

'ndaki `TRUE` İşlev bir en son döndürme kullanıyorsa, aksi takdirde, döndürür `FALSE` .

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
