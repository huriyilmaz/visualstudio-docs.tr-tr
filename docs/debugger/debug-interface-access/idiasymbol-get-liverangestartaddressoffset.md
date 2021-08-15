---
description: Yerel sembolün geçerli olduğu aralığın başlangıç adresinin uzaklık bölümünü döndürür.
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3ce82f2eb649aed098508e20ebb9e7f2d6bf4fae63dd1fa3ae8f464607fbd8a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344514"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Yerel sembolün geçerli olduğu aralığın başlangıç adresinin uzaklık bölümünü döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parametreler
 `offset`

[out] Başlangıç adres aralığının uzaklık bölümünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

> [!NOTE]
> Döndürülen hata kodu, sembolün canlı aralık bilgilerine sahip olmadığını gösterir.

## <a name="remarks"></a>Açıklamalar
 Bölüm ve uzaklık tarafından oluşturulan adres, sembolün geçerli olduğu aralığın başlangıcıdır.

 Adresin bölüm bölümünü almak için [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
