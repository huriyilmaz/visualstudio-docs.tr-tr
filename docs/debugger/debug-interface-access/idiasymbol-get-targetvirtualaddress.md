---
description: Bir thunk hedefinin sanal adresini (VA) alan.
title: IDiaSymbol::get_targetVirtualAddress | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626660"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
Bir thunk hedefinin sanal adresini (VA) alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_targetVirtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bir thunk hedefinin VA'sı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca sembol, [SymTagEnum Enum değeri olarak değerine sahipse](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` geçerlidir.

 "Thunk", 32 bit bellek adres alanı (düz adres alanı olarak da bilinir) ile 16 bit adres alanı (kesimli adres alanı olarak bilinir) arasında dönüştürmeler yapılan bir kod parçasıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
