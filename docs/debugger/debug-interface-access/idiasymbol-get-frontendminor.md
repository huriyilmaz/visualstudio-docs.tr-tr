---
title: 'IDiaSymbol:: get_frontEndMinor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b329cd69d010cba4e3667bde0d7b976389037bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740640"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Ön uç ikincil sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Ön. son ikincil sürüm numarasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> `S_FALSE` dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Derleyici genellikle iki birincil öğeden oluşur: kaynak kodu bir ara forma ayrıştırmayı işleyen ön uç (Ayrıştırıcı) ve ara formu derlemeye dönüştüren bir arka uç (kod Oluşturucu). Ön uç için arka uçtan farklı bir sürüme sahip olması seyrek değildir.

 Ön uç veya arka uç sürüm numarası üç bölümden oluşur: \<major >. \<minor >. \<build >, \<major > Ana sürüm numarasıdır, \<minor > ikincil sürüm numarasıdır ve \<build > yapı numarasıdır. Örneğin, 13.10.3077.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)