---
title: 'IDiaSymbol:: get_intro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740342"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
İşlevin bir sanal işlev olduğunu belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
`pRetVal`

dışı İşlev tanıtım sanal ise `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="example"></a>Örnek

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Hem `A::f1` hem de `B::f1` sanal işlevlerdir, ancak `A::f1` tanıtım sanal olur.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
