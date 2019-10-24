---
title: 'IDiaSymbol:: get_hasEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f08cd539d3042ff0715a5c84445e4cc40214a41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740546"
---
# <a name="idiasymbolget_haseh"></a>IDiaSymbol::get_hasEH
İşlevin yönetilmeyen C++stil özel durum işleme (örneğin, bir try/catch bloğu) içerip içermediğini belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı İşlevde herhangi bir C++stil özel durum işleme varsa `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)