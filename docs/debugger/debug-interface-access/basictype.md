---
title: BasicType | Microsoft Docs
description: Visual Studio hata ayıklama arabirimi erişim SDK 'sında bir sembolün temel türünü belirten BasicType numaralandırması hakkında başvuru bilgileri bulun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a86a25d02b1aa51e49d80b71dbd37b2aa4c2d103
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865591"
---
# <a name="basictype"></a>BasicType
Simgenin temel türünü belirtir.

## <a name="syntax"></a>Syntax

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Öğeler
btNoType temel tür belirtilmedi.

btVoid temel türü bir `void` .

btChar temel türü bir `char` (C/C++ türü).

btWChar temel türü, geniş bir (Unicode) karakterdir ( `WCHAR` ).

btInt temel türü `signed int` (C/C++ türü).

Btuınt temel türü `unsigned int` (C/C++ türü).

btFloat temel türü bir kayan noktalı sayıdır ( `FLOAT` ).

btBCD temel türü ikili kodlanmış bir Decimal ( `BCD` ).

btBool temel türü bir Boole değeri ( `BOOL` ).

btLong temel türü bir `long int` (C/C++ türü).

btULong temel türü bir `unsigned long int` (C/C++ türü).

btCurrency temel türü para birimidir.

btDate temel türü tarih/saat ( `DATE` ).

btVariant temel türü bir değişken türü yapısıdır ( `VARIANT` ).

btComplex temel türü karmaşık bir sayıdır.

btBit temel türü bir bittir.

btBSTR temel türü temel veya ikili dizedir ( `BSTR` ).

btHresult temel türü bir `HRESULT` .

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
