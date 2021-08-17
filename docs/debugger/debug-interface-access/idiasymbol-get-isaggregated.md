---
description: Veri simgesinin bir toplama veya sembol koleksiyonuna ait olup olmadığını belirten bir bayrak alma; derleyici, toplanan sembolleri ayrı varlıklar olarak işlese de, bunlar aslında tek bir büyük sembolün parçasıdır.
title: IDiaSymbol::get_isAggregated | Microsoft Docs
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
ms.openlocfilehash: 1a870a6e868848f0d2c5b4c597440bc5214df31cb951fe8259cec633afc5306b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420681"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Veri simgesinin bir toplama veya sembol koleksiyonuna ait olup olmadığını belirten bir bayrak alma; derleyici, toplanan sembolleri ayrı varlıklar olarak işlese de, bunlar aslında tek bir büyük sembolün parçasıdır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] Veriler üst simgeden ayrılmış sembollerin bir toplama parçası ise döndürür; aksi takdirde `TRUE` `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) yöntemi, toplanan `TRUE` sembollerin üst öğesi olan sembole göredir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)
