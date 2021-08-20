---
description: Veri simgesinin bir toplamaya mı yoksa diğer sembollerin koleksiyonuna mı bölündü? derleyici, daha büyük bir sembolün gerçekten parçası olsalar bile sembolleri ayrı varlıklar olarak davranır.
title: IDiaSymbol::get_isSplitted | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c025460f04cbd2d9eb5546f434ff990584fa7e26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121476"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Veri simgesinin bir toplamaya mı yoksa diğer sembollerin koleksiyonuna mı bölündü? derleyici, daha büyük bir sembolün gerçekten parçası olsalar bile sembolleri ayrı varlıklar olarak davranır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] Sembol `TRUE` bir sembol toplamaya bölündü ise döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) yöntemi, bölünmüş bir sembolün parçası `TRUE` olan tüm semboller için döndürür.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
