---
description: Bu simgeyle temsil edilen nesne tarafından kullanılan bit veya bellek bayt sayısını verir.
title: IDiaSymbol::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a95d21701eae7e780c8d191c6db5394170a571a91674d8d2d22975c4852b54ac
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454698"
---
# <a name="idiasymbolget_length"></a>IDiaSymbol::get_length
Bu simgeyle temsil edilen nesne tarafından kullanılan bit veya bellek bayt sayısını verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bu simgeyle temsil edilen nesne tarafından kullanılan bellek bayt veya bit sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sembolün [LocationType Numaralama değeri](../../debugger/debug-interface-access/locationtype.md) ise, bu yöntem tarafından döndürülen uzunluk bittir; aksi takdirde, uzunluk diğer tüm konum türleri için bayt `LocIsBitField` cinsindendir.

## <a name="example"></a>Örnek

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
