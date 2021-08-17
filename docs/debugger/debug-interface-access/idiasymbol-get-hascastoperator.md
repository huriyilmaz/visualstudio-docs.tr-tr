---
description: Kullanıcı tanımlı veri türünün tanımlanmış herhangi bir türe sahip olup olmadığını belirten bir bayrak alınır.
title: IDiaSymbol::get_hasCastOperator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasCastOperator method
ms.assetid: a21114a6-56a3-4e8a-a65f-58ec2a0a8908
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 89ca0e736cddf33f72fcc08ea23bcafcbdd6fd0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091007"
---
# <a name="idiasymbolget_hascastoperator"></a>IDiaSymbol::get_hasCastOperator
Kullanıcı tanımlı veri türünün tanımlanmış herhangi bir türe sahip olup olmadığını belirten bir bayrak alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasCastOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Kullanıcı tanımlı `TRUE` veri türünde tanımlanmış herhangi bir türe sahipse bir döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
