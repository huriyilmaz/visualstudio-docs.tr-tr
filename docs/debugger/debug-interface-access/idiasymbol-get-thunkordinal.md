---
title: 'IDiaSymbol:: get_thunkOrdinal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 276cb0ed42f884f2be3b10d82fd8561c6b9aa20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853508"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Bir işlevin dönüştürücü türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir işlevin dönüştürücü türünü belirten [THUNK_ORDINAL sabit](../../debugger/debug-interface-access/thunk-ordinal.md) listesi numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca sembol bir [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değeri olarak sembolü ise geçerlidir `SymTagThunk` .

 "Dönüştürücü", 32 bitlik bir bellek adres alanı (düz adres alanı olarak da bilinir) ve 16 bit adres alanı (bölümlenmiş adres alanı olarak bilinir) arasında dönüştürme yapan bir kod parçasıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL Numaralandırması](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)