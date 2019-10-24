---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745259"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Adres eşlemesindeki bir girişi açıklar.

## <a name="syntax"></a>Sözdizimi

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Öğeler
A görüntüsünde göreli bir sanal adres (RVA) `rva`.

göreli sanal adres `rva` `rvaTo` B görüntüsünde eşlenir.

## <a name="remarks"></a>Açıklamalar
Adres eşlemesi, bir görüntü düzeninden (A) diğerine (B) bir çeviri sağlar. @No__t_1 tarafından sıralanan `DiaAddressMapEntry` yapılarının bir dizisi, bir adres haritasını tanımlar.

Bir adresi `addrA`, görüntü A 'daki bir adrese çevirmek için, `addrB`, görüntü B 'de aşağıdaki adımları uygulayın:

1. @No__t_0 için haritada arama yapın, en büyük `rva` `addrA` küçüktür veya eşittir.

2. @No__t_0 ayarlayın.

3. @No__t_0 ayarlayın.

    [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemine bir dizi `DiaAddressMapEntry` yapısı geçirilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
