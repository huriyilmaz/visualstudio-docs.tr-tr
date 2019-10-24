---
title: Sembol konumları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f972d0d072aa36cab608c85305588f6bbd5d47d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738535"
---
# <a name="symbol-locations"></a>Simge Konumları
Çoğu simgenin görüntü dosyası içinde tanımlı bir konumu vardır. Bir simgenin konumu, [LocationType numaralandırma](../../debugger/debug-interface-access/locationtype.md) numaralandırmasındaki bir değerle belirtilir. Sembol, konumuna bağlı olarak ek özellikleri destekleyebilir.

 Aşağıdaki tabloda en yaygın olarak kullanılan konum türleri ve bunların ek özellikleri gösterilmektedir.

|Konum türü|Ek özellikler|
|-------------------|---------------------------|
|`LocIsNull`|yok|
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (göreli sanal adresler etkinse)<br /><br /> [IDiaSymbol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (görüntü tabanı sıfır dışında olarak ayarlandıysa)|
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)
- [IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)
- [IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)
- [IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)
- [IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)
- [IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)
- [IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)