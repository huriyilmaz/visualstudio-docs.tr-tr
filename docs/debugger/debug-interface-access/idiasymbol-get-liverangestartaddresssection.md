---
description: Yerel sembolün geçerli olduğu aralığın başlangıç adresinin bölüm bölümünü döndürür.
title: 'IDiaSymbol:: get_liveRangeStartAddressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 93efcf7412835fa9a4f1146d293d2d4e4d25e05f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105452"
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
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Döndürülen bir hata kodu, simgenin canlı Aralık bilgilerine sahip olmadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bölüm ve konum tarafından oluşturulan adres, simgenin geçerli olduğu aralığın başlangıcıdır.

 Adresin konum kısmını almak için [IDiaSymbol:: get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)kullanın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
