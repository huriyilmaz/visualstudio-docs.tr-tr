---
title: 'IDiaSymbol:: get_code | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_code method
ms.assetid: 5f425fa3-7ba6-4979-8b3e-0fcd06cbba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b34714ccd23929d4aaa3ea734fc80941d04103dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464095"
---
# <a name="idiasymbolget_code"></a>IDiaSymbol::get_code
Simgenin bir kod adresine başvuru yapıp kullanmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_code ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Simgenin bir kod adresine başvuruyorsa, aksi takdirde döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Description|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)