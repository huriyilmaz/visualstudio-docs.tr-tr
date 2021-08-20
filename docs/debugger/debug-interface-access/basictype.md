---
title: BasicType | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK'sı içinde bir sembolün temel türünü belirten BasicType Visual Studio başvuru bilgilerini bulun.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9c59e66b73767b5ee5c6787fe0155ad1a2345161
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129522"
---
# <a name="basictype"></a>BasicType
Sembolün temel türünü belirtir.

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
btNoType Temel tür belirtilmemiş.

btVoid Basic türü bir `void` 'dır.

btChar Basic türü bir `char` (C/C++ türü).

btWChar Basic türü geniş (Unicode) bir karakterdir ( `WCHAR` ).

btInt Basic türü `signed int` (C/C++ türü).

btUInt Basic türü `unsigned int` (C/C++ türü).

btFloat Basic türü bir kayan nokta numarasıdır ( `FLOAT` ).

btBCD Temel türü ikili kodlu ondalıktır ( `BCD` ).

btBool Basic türü bir Boolean ( ). `BOOL`

btLong Basic türü bir `long int` (C/C++ türü).

btULong Basic türü bir `unsigned long int` (C/C++ türü).

btCurrency Temel türü para birimidir.

btDate Temel türü tarih/saat `DATE` ( ).

btVariant Basic türü bir değişken türü yapısıdır ( `VARIANT` ).

btComplex Basic türü karmaşık bir sayıdır.

btBit Basic türü biraz.

btBSTR Temel türü, temel veya ikili dizedir ( `BSTR` ).

btHresult Basic türü bir `HRESULT` 'dır.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
