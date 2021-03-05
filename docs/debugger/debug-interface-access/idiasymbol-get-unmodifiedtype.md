---
description: Bu sembolün orijinal türünü alır.
title: 'IDiaSymbol:: get_unmodifiedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98c4256dfd0bc6fb532f51ee7d7d16cfdb7e0f8f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160577"
---
# <a name="idiasymbolget_unmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Bu sembolün orijinal türünü alır. [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) bir türe ayarlandığında kullanın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_unmodifiedType( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bu sembolün orijinal türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Geçerli tür, döndürülen özgün türün bir değişimdir. Bir simgenin özgün türü, ilk olarak simgenin türü ve sonra özgün tür için döndürülen tür için bir alan tarafından belirlenebilir. Bazı sembollerin özgün türde değiştirilmiş bir türü olamayacağını unutmayın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
