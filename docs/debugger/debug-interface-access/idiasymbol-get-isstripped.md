---
title: 'IDiaSymbol:: get_isStripped | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12fac0c26c53695dcc9b42794337a7feaea6b0fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740017"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
Özel simgelerin sembol dosyasından bırakılıp nakledilmediğini belirten bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isStripped(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı Özel semboller sembol dosyasından kaldırılmışsa `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik `SymTagExe` sembol türünden (bkz. [exe](../../debugger/debug-interface-access/exe.md)) kullanılabilir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)