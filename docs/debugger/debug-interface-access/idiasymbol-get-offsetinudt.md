---
title: 'IDiaSymbol:: get_offsetInUdt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offsetInUdt method
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0eeffba743d7fae1d473c45eb350fbfc8bcd0b9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739566"
---
# <a name="idiasymbolget_offsetinudt"></a>IDiaSymbol::get_offsetInUdt
UDT içindeki bir üyenin Kullanıcı tanımlı türünün (UDT) başlangıcına olan sapmayı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_offsetInUdt( 
   DWORD* pRetVal)
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Sembol konumunun bayt cinsinden sapmasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu işlev, iyileştirilmiş bir derlemede yalnızca yerel kayıtlarda kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)