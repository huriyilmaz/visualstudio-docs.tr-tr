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
ms.workload:
- multiple
ms.openlocfilehash: bdac0233901ac8571bbfb2a5d6659adf69e35298
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149195"
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
