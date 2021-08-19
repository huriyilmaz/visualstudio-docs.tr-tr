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
ms.openlocfilehash: d86b78041bd4f78a382c82e95f4b330e7ddd5d2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147145"
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
