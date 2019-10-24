---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738644"
---
# <a name="locationtype"></a>LocationType
Bir sembolde bulunan konum bilgilerinin türünü gösterir.

## <a name="syntax"></a>Sözdizimi

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
`LocIsNull` konum bilgileri kullanılamıyor.

`LocIsStatic` konum statiktir.

`LocIsTLS` konumu iş parçacığı yerel depolama alanında.

`LocIsRegRel` konum kayıt göreli.

`LocIsThisRel` konum `this` görelidir.

`LocIsEnregistered` konum bir yazmaç içinde.

`LocIsBitField` konum bir bit alanıdır.

`LocIsSlot` konum bir Microsoft ara dili (MSIL) yuvadır.

`LocIsIlRel` konum MSIL ile ilişkilidir.

`LocInMetaData` konumu meta verilerde.

`LocIsConstant` konum sabit bir değerde.

Bu Numaralandırmadaki konum türlerinin sayısını `LocTypeMax`.

## <a name="remarks"></a>Açıklamalar
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) arabirimi için kullanılabilen özellikler simgenin görüntü dosyası içindeki konumuna bağlıdır. Daha fazla bilgi için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).

Bu Numaralandırmadaki değerler [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) yöntemi çağrısıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
