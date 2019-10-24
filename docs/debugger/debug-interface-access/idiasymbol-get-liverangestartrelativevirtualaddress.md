---
title: 'IDiaSymbol:: get_liveRangeStartRelativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea82e9d1dee4b82e78ea3f6409acfdcfc30b2a27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739888"
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
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Döndürülen göreli sanal adres, simgenin geçerli olduğu aralığın başlangıcıdır.

> [!NOTE]
> Döndürülen bir hata kodu, simgenin canlı Aralık bilgilerine sahip olmadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)