---
description: LocationType numaralandırması) LocIsEnregistered olarak ayarlandığında konumun kayıt göstergesini alır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 715fc20baafeaf6ed7adb8790b84daedfc9d3b19
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147235"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandığında konumun kayıt göstergesini alır `LocIsEnregistered` .

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
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sembol bir yazmaç ile ilişkili ise, yani sembolün [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandıysa `LocIsRegRel` , bu yöntemi, simgenin bulunduğu `get_registerId` kaydın sapmasını almak için [ıdiasymbol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) yöntemine bir çağrı izler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
