---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2fafbb25d52df6082736431727222c788d73476
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461219"
---
# <a name="locationtype"></a>LocationType
Bir sembolde bulunan konum bilgilerinin türünü gösterir.

## <a name="syntax"></a>Syntax

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Öğeler
`LocIsNull`Konum bilgileri kullanılamıyor.

`LocIsStatic`Konum statiktir.

`LocIsTLS`Konum, iş parçacığı yerel depolama alanında.

`LocIsRegRel`Konum, kayıt göreli.

`LocIsThisRel`Konum `this` -göreli.

`LocIsEnregistered`Konum bir yazmaç içinde.

`LocIsBitField`Konum bir bit alanıdır.

`LocIsSlot`Konum bir Microsoft ara dil (MSIL) yuvadır.

`LocIsIlRel`Konum MSIL ile ilişkilidir.

`LocInMetaData`Konum meta verilerde.

`LocIsConstant`Konum sabit bir değerde.

`LocTypeMax`Bu Numaralandırmadaki konum türlerinin sayısı.

## <a name="remarks"></a>Açıklamalar
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) arabirimi için kullanılabilen özellikler simgenin görüntü dosyası içindeki konumuna bağlıdır. Daha fazla bilgi için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).

Bu Numaralandırmadaki değerler [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) metoduna yapılan bir çağrı tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
