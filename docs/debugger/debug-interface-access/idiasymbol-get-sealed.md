---
description: Sınıf veya yöntemin korumalı olup olmadığını belirten bir bayrağını alın.
title: IDiaSymbol::get_sealed | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 700bdb997a11ce2d29ba84812e12edd5d8462d39f97acab63857ea70a00c12ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379793"
---
# <a name="idiasymbolget_sealed"></a>IDiaSymbol::get_sealed
Sınıf veya yöntemin korumalı olup olmadığını belirten bir bayrağını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_sealed( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sınıf `TRUE` veya yöntem korumalı ise döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Korumalı bir sınıf, temel sınıf olarak kullanılamaz. Korumalı bir yöntemin üzerinden overidden edilemez.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
