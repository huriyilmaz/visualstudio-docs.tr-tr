---
description: Veri sembolünün sembol toplamanın veya bir koleksiyonunun bir parçası olup olmadığını belirten bir bayrak alır; Derleyici toplanmış sembolleri ayrı varlıklar olarak değerlendirir, ancak bunlar aslında tek bir büyük simgenin parçalarından oluşur.
title: 'IDiaSymbol:: get_isAggregated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ebf6035fcec95fff5849d7aa472ed97f9d9cc0b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044185"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Veri sembolünün sembol toplamanın veya bir koleksiyonunun bir parçası olup olmadığını belirten bir bayrak alır; Derleyici toplanmış sembolleri ayrı varlıklar olarak değerlendirir, ancak bunlar aslında tek bir büyük simgenin parçalarından oluşur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` Verilerin bir üst sembolden bölünen bir sembol toplamasının parçası olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 [IDiaSymbol:: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) yöntemi, `TRUE` toplanan simgelerin üst öğesi olan sembol içindir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)
