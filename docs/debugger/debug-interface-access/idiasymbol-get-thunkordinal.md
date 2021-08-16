---
description: Bir işlevin dönüştürücü türünü alır.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 28c8cc04bd3b6869bfde35ae5dcb7bc0a88f3ce5c7d5a3d9ab4c7d01268ea82f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404685"
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
