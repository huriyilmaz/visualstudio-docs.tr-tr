---
title: 'IDiaSymbol:: get_registerId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739458"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) `LocIsEnregistered` olarak ayarlandığında konumun kayıt göstergesini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Konumun kayıt göstergesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri, özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sembol bir yazmaç ile ilişkili ise, yani sembolün [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` olarak ayarlandıysa, `get_registerId` yöntemini ve sonra simgenin bulunduğu kaydın sapmasını almak Için [IDiaSymbol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) yöntemine bir çağrı yapın. kutusunun.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)