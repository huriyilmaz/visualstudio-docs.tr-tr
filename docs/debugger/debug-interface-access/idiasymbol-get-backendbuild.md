---
description: Derleyicinin arka uç derleme numarasını alır.
title: 'IDiaSymbol:: get_backEndBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a2e7743c65ebbc6d00ef1e6367bf123ce7a65479312a22d8042b1e4afa73ab30
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454802"
---
# <a name="idiasymbolget_backendbuild"></a>IDiaSymbol::get_backEndBuild
Derleyicinin arka uç derleme numarasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_backEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Arka uç derleme numarasını döndürür. Bkz. açıklamalar.

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
