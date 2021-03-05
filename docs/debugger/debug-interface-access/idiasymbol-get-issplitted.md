---
description: Veri sembolünün diğer sembollerin toplama veya toplama göre bölünmeyeceğini belirten bir bayrak alır; Derleyici, sembolleri büyük bir sembolün gerçekten bir parçası olsalar bile ayrı varlıklar olarak değerlendirir.
title: 'IDiaSymbol:: get_isSplitted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5dd9807928ca5f1b8d2e3b20c5de3ec30adc70db
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162056"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Veri sembolünün diğer sembollerin toplama veya toplama göre bölünmeyeceğini belirten bir bayrak alır; Derleyici, sembolleri büyük bir sembolün gerçekten bir parçası olsalar bile ayrı varlıklar olarak değerlendirir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` Simgenin bir sembol toplamasına bölündüğünü döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 [IDiaSymbol:: get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) yöntemi, `TRUE` bölünmüş bir simgenin parçası olan tüm semboller için döndürülür.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
