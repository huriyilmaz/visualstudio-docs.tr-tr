---
description: Kullanıcı tanımlı veri türünün aşırı yüklenmiş işleçlere sahip olup olmadığını belirten bir bayrak alır.
title: 'IDiaSymbol:: get_overloadedOperator | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_overloadedOperator method
ms.assetid: 257a9894-e980-47ae-bdc0-c5e2293ea734
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c30cfd825379e88293aa8f32b9b994798ea5f8a8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155868"
---
# <a name="idiasymbolget_overloadedoperator"></a>IDiaSymbol::get_overloadedOperator
Kullanıcı tanımlı veri türünün aşırı yüklenmiş işleçlere sahip olup olmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_overloadedOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Kullanıcı tanımlı veri türünün aşırı yüklenmiş işleçler varsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
