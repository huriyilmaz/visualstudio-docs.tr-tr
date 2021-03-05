---
description: Yerel simgenin geçerli olduğu adres aralığının başlangıcını döndürür.
title: 'IDiaSymbol:: get_liveRangeStartRelativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 39ee479721a7168aae5504b58495cfb536f5b38a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156043"
---
# <a name="idiasymbolget_liverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Yerel simgenin geçerli olduğu adres aralığının başlangıcını döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>Parametreler
 `address`

dışı Adres aralığının başlangıcını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Döndürülen göreli sanal adres, simgenin geçerli olduğu aralığın başlangıcıdır.

> [!NOTE]
> Döndürülen bir hata kodu, simgenin canlı Aralık bilgilerine sahip olmadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
