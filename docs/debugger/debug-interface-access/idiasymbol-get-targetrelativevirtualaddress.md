---
description: Bir thunk hedefinin göreli sanal adresini (RVA) alan.
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f5912453c7104b9d6b5f15c46c195413f7d82194505d203a8256fb124409d2a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362964"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Bir thunk hedefinin göreli sanal adresini (RVA) alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bir thunk hedefinin RVA'sı döndürür.

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
