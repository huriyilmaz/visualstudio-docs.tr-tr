---
description: Thunk türlerini gösterir.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c2ed7f7945c9ab4fb51d8ad434535d48e30b26ee12cbb880ed72500330d2c966
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240443"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Thunk türlerini gösterir.

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
THUNK_ORDINAL_NOTYPE standart thunk.

THUNK_ORDINAL_ADJUSTOR `this` ayar ayarı.

THUNK_ORDINAL_VCALL çağrısı thunk.

THUNK_ORDINAL_PCODE P-code thunk.

THUNK_ORDINAL_LOAD gecikme süresi.

THUNK_ORDINAL_TRAMP_INCREMENTAL artımlı çizgi thunk (çağrılardan bir bellek boşluğundan diğerine geri sıçramak için bir satır thunk kullanılır).

THUNK_ORDINAL_TRAMP_BRANCHISLAND dal noktası kılavuz çizgisi.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_thunkOrdinal yöntemi çağrısından](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
