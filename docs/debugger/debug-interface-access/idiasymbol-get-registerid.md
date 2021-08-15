---
description: LocationType Numaralandırıcısı) LocIsEnregistered' olarak ayarlanırken konumun yazmaç belirleyicisi alınır.
title: IDiaSymbol::get_registerId | Microsoft Docs
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
ms.openlocfilehash: 2a82c9b0cc7c2db8ad7b0bc5329ab74fb7f4ef1e274c5366e71afd3ff665ce1d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240467"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[LocationType Enumeration](../../debugger/debug-interface-access/locationtype.md) olarak ayarlanırken konumun yazmaç tasarımını `LocIsEnregistered` alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Konumun yazmaç tasarımını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sembol bir yazmaçla göreli ise, yani sembolün [LocationType](../../debugger/debug-interface-access/locationtype.md) Numaralama değeri olarak ayarlanırsa, sembol bulunduğu yazmacın uzaklığı almak için `LocIsRegRel` yöntemini `get_registerId` [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) yöntemine yapılan bir çağrıyla kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
