---
title: 'IDiaSymbol:: get_registerId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f252d02a137ada627c0c546e1f1ac79118f76de9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462478"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandığında konumun kayıt göstergesini alır `LocIsEnregistered` .

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Konumun kayıt göstergesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sembol bir yazmaç ile ilişkili ise, yani sembolün [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandıysa `LocIsRegRel` , bu yöntemi, simgenin bulunduğu `get_registerId` kaydın sapmasını almak için [ıdiasymbol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) yöntemine bir çağrı izler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)