---
description: Ön uç derleme numarasını alır.
title: 'IDiaSymbol:: get_frontEndBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 64c160d0275c2027ec5d2e128b8319bde20d965c19a00f370c317c27726d50f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454784"
---
# <a name="idiasymbolget_frontendbuild"></a>IDiaSymbol::get_frontEndBuild
Ön uç derleme numarasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_frontEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Ön uç derleme numarasını döndürür. Bkz. açıklamalar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Derleyici genellikle iki birincil öğeden oluşur: kaynak kodu bir ara forma ayrıştırmayı işleyen ön uç (Ayrıştırıcı) ve ara formu derlemeye dönüştüren bir arka uç (kod Oluşturucu). Ön uç için arka uçtan farklı bir sürüme sahip olması seyrek değildir.

 Ön uç veya arka uç sürüm numarası üç bölümden oluşur: \<major> . \<minor> . \<build> , burada \<major> ana sürüm numarasıdır, \<minor> ikincil sürüm numarasıdır ve \<build> yapı numarasıdır. Örneğin, 13.10.3077.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
