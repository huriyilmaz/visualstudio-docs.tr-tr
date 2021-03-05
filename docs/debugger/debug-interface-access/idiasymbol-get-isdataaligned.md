---
description: Kullanıcı tanımlı türün (UDT) belirli bir bellek sınırına hizalanıp Hizalanmadığını belirten bir bayrak alır.
title: 'IDiaSymbol:: get_isDataAligned | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e32df5e095f7f7af332e29a8f9899d6f1f5351e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156204"
---
# <a name="idiasymbolget_isdataaligned"></a>IDiaSymbol::get_isDataAligned
Kullanıcı tanımlı türün (UDT) belirli bir bellek sınırına hizalanıp Hizalanmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` Udt bir bellek sınırına hizalanmışsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik genellikle yürütülebilir dosya, varsayılan olmayan veri hizalamayla derlendiğinde ayarlanır. Örneğin, Microsoft C++ derleyicisi, veri hizalamasını <em>#</em> bir bayt değeri olan/ZP komut satırı seçeneğiyle değiştirebilir *#* .

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
