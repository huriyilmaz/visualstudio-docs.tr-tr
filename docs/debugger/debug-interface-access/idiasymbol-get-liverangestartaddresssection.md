---
title: 'IDiaSymbol:: get_liveRangeStartAddressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a23f0661d8af6417d754fd7a71c66c5dd3ef1135
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739900"
---
# <a name="idiasymbolget_liverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Yerel sembolün geçerli olduğu aralığın başlangıç adresinin bölüm bölümünü döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Parametreler
 `section`

dışı Başlangıç adres aralığının bölüm bölümünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Döndürülen bir hata kodu, simgenin canlı Aralık bilgilerine sahip olmadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bölüm ve konum tarafından oluşturulan adres, simgenin geçerli olduğu aralığın başlangıcıdır.

 Adresin konum kısmını almak için [IDiaSymbol:: get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)kullanın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)