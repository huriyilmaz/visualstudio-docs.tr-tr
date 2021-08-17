---
description: Bir simgede yer alan konum bilgilerine ilişkin tür gösterir.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d68e541060c07a523af001558f2804eed35d498d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097639"
---
# <a name="locationtype"></a>LocationType
Bir simgede yer alan konum bilgilerine ilişkin tür gösterir.

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
`LocIsNull` Konum bilgileri kullanılamıyor.

`LocIsStatic` Konum statiktir.

`LocIsTLS` Konum, iş parçacığı yerel depolamadadır.

`LocIsRegRel` Konum register-relative'dır.

`LocIsThisRel` Konum `this` görelidir.

`LocIsEnregistered` Konum bir yazmama içindedir.

`LocIsBitField` Konum bir bit alanındadır.

`LocIsSlot` Konum bir Microsoft Ara Dil (MSIL) yuvasıdır.

`LocIsIlRel` Konum MSIL görelidir.

`LocInMetaData` Konum meta verilerdedir.

`LocIsConstant` Konum sabit bir değerdedir.

`LocTypeMax` Bu numaralamada yer alan konum türlerinin sayısı.

## <a name="remarks"></a>Açıklamalar
[IDiaSymbol arabiriminde](../../debugger/debug-interface-access/idiasymbol.md) kullanılabilen özellikler, simgenin görüntü dosyasındaki konumuna bağlıdır. Daha fazla bilgi için [bkz. Sembol Konumları.](../../debugger/debug-interface-access/symbol-locations.md)

Bu numaralamada yer alan değerler [IDiaSymbol::get_locationType yöntemine yapılan bir çağrıyla](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
