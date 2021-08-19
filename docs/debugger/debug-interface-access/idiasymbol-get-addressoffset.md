---
description: Adres konumunun uzaklık bölümünü alın.
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2dcbee6f04a61bb21ffc1071b200297ecd0b3890
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081304"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Adres konumunun uzaklık bölümünü alın. [LocationType Enumeration olarak ayarlanırken](../../debugger/debug-interface-access/locationtype.md) `LocIsStatic` kullanın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Adres konumunun kaydırma bölümünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bir dış DLL'de bulunan statik üyeler için bu yöntem tarafından döndürülen uzaklık 0 olabilir çünkü bu yöntem üyenin sanal adresini elde etmek için kullanır. Sanal adresler yalnızca [IDiaSession arabiriminde IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemi DLL'nin yük adresini belirten sıfır olmayan bir parametreyle çağrıldıklarında geçerlidir. [](../../debugger/debug-interface-access/idiasession.md)

 Bir adresin bölüm bölümünü almak için [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) yöntemini arayın.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
