---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cae8159c893229f02e9598e932d7bc19efc2f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468681"
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
