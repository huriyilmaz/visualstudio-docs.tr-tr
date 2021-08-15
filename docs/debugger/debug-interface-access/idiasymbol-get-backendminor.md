---
description: Derleyicinin arka uç ikincil sürüm numarasını alın.
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b48c3a2e5042137ceed4c8655ec2d080c597f99d2c060b3b19a7130f31372564
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312055"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
Derleyicinin arka uç ikincil sürüm numarasını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Arka uç ikincil sürüm numarasını döndürür. Bkz. Açıklamalar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

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
