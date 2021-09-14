---
description: Adres eşlemesinde bir girişi açıklar.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630633"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Adres eşlemesinde bir girişi açıklar.

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Öğeler
`rva` A görüntüsünde göreli bir sanal adres (RVA).

`rvaTo` Göreli sanal `rva` adres, B görüntüsünde ile eşlenmiş.

## <a name="remarks"></a>Açıklamalar
Adres haritası, bir görüntü düzeninden (A) diğerine (B) çeviri sağlar. tarafından `DiaAddressMapEntry` sıralanmış bir yapı dizisi, `rva` bir adres eşlemesi tanımlar.

A görüntüsünde bir `addrA` adresi, B görüntüsünde ise `addrB` adresine çevirmek için aşağıdaki adımları gerçekleştirin:

1. Eşlemede girdisi için arama ve en `e` büyük değerden `rva` küçük veya `addrA` eşittir.

2. 'i `delta = addrA - e.rva` ayarlayın.

3. 'i `addrB = e.rvaTo + delta` ayarlayın.

    Yapı dizisi `DiaAddressMapEntry` [IDiaAddressMap::set_addressMap yöntemine](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: dia2.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
