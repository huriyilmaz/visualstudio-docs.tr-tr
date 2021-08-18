---
description: Modülün /Z7, /Zi, /ZI (Hata Ayıklama Bilgileri Biçimi)) derleyici anahtarıyla derlenmiş olup olmadığını belirten bir bayrak verir.
title: IDiaSymbol::get_editAndContinueEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 14884bee6ab80525f1e5b2ed1e26ca72658742d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036178"
---
# <a name="idiasymbolget_editandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
Modülün [/Z7, /Zi, /ZI (Hata](/cpp/build/reference/z7-zi-zi-debug-information-format) Ayıklama Bilgileri Biçimi) derleyici anahtarıyla derlenmiş olup olmadığını belirten bir bayrak verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_editAndContinueEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] `TRUE` Edit-and-continue derlemede etkinleştirildiyse döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/Z7, /Zi, /ZI (Hata Ayıklama Bilgileri Biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format)
