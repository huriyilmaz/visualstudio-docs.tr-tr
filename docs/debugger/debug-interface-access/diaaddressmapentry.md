---
description: Adres eşlemesindeki bir girişi açıklar.
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4c5ac207ec1fc66554264d14f2aa9f0dccbb3773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036683"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Adres eşlemesindeki bir girişi açıklar.

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Öğeler
`rva` A görüntüsündeki göreli bir sanal adres (RVA).

`rvaTo` Göreli sanal adres `rva` B görüntüsünde eşlenir.

## <a name="remarks"></a>Açıklamalar
Adres eşlemesi, bir görüntü düzeninden (A) diğerine (B) bir çeviri sağlar. `DiaAddressMapEntry`Sıralanmış bir yapı dizisi `rva` bir adres haritasını tanımlar.

Bir adresi çevirmek için, `addrA` A görüntüsünde adrese, `addrB` görüntü B ' de aşağıdaki adımları gerçekleştirin:

1. Haritada, `e` en büyükten `rva` küçük veya eşit olan girdiyi arayın `addrA` .

2. Ayarlayın `delta = addrA - e.rva` .

3. Ayarlayın `addrB = e.rvaTo + delta` .

    `DiaAddressMapEntry`Yapı dizisi [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metoduna geçirilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
