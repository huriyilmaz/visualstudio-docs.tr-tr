---
title: 'IDiaSymbol:: get_targetVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe19daf3271006e177677d490ccccd89ee293af2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461825"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
Bir dönüştürücü hedefinin sanal adresini (VA) alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_targetVirtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir dönüştürücü hedefinin VA değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca sembol bir [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değeri olarak sembolü ise geçerlidir `SymTagThunk` .

 "Dönüştürücü", 32 bitlik bir bellek adres alanı (düz adres alanı olarak da bilinir) ve 16 bit adres alanı (bölümlenmiş adres alanı olarak bilinir) arasında dönüştürme yapan bir kod parçasıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)