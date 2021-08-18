---
description: Bir dönüştürücü hedefinin sanal adresini (VA) alır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8c9024683d25679794f3fe29ea9a01233ca9e443
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097655"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
Bir dönüştürücü hedefinin sanal adresini (VA) alır.

## <a name="syntax"></a>Sözdizimi

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
