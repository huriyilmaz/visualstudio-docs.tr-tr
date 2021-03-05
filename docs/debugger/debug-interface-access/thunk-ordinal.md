---
description: Dönüştürücü türlerini belirtir.
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8d9fe78eedd0166594daf43093aa525e3d8d3e88
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161594"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Dönüştürücü türlerini belirtir.

## <a name="syntax"></a>Syntax

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Öğeler
Standart dönüştürücü THUNK_ORDINAL_NOTYPE.

Bir `this` ayarlancı dönüştürücü THUNK_ORDINAL_ADJUSTOR.

Sanal Çağrı dönüştürücü THUNK_ORDINAL_VCALL.

THUNK_ORDINAL_PCODE P kodu dönüştürücü.

THUNK_ORDINAL_LOAD gecikme yükleme dönüştürücü.

THUNK_ORDINAL_TRAMP_INCREMENTAL artımlı trampoline dönüştürücü (bir trampoline dönüştürücü, bir bellek alanından diğerine yapılan çağrıları sıçramalar için kullanılır).

THUNK_ORDINAL_TRAMP_BRANCHISLAND dal noktası trampoline dönüştürücü.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metoduna yapılan çağrıdan döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
