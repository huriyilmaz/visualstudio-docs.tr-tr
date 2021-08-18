---
description: Ön uç ikincil sürüm numarasını alın.
title: IDiaSymbol::get_frontEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e0e49546da264bff8c1e9bddd32e8a973223c02d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036154"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Ön uç ikincil sürüm numarasını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Front.end ikincil sürüm numarasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Derleyici genellikle iki birincil öğeden oluşur: kaynak kodu bir ara forma ayrıştırmayı ele alan ön uç (ayrıştırıcı) ve ara formu derlemeye dönüştüren bir arka uç (kod oluşturucu). Ön uçta arka uçtan farklı bir sürüme sahip olmak yaygın bir durum değildir.

 Ön uç veya arka uç sürüm numarası üç parçadan oluşur: . . , burada ana sürüm numarasıdır, ikincil sürüm numarasıdır ve \<major> \<minor> derleme \<build> \<major> \<minor> \<build> numarasıdır. Örneğin, 13.10.3077.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
