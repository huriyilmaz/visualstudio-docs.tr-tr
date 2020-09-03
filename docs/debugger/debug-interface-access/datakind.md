---
title: Veri türü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2423646976744da17d3e904246ac74f8b2e75f41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468709"
---
# <a name="datakind"></a>DataKind
Bir veri değerinin belirli kapsamını gösterir.

## <a name="syntax"></a>Syntax

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Öğeler
Dataısunknown veri simgesi belirlenemiyor.

Dataıslocal veri öğesi yerel bir değişkendir.

Dataısstaticlocal veri öğesi statik bir yerel değişkendir.

DataIsParam veri öğesi biçimsel bir parametredir.

DataIsObjectPtr veri öğesi bir nesne işaretçisidir ( `this` ).

Dataısfilestatic veri öğesi, dosya kapsamlı bir değişkendir.

Dataısglobal veri öğesi genel bir değişkendir.

DataIsMember veri öğesi bir nesne üyesi değişkenidir.

Dataısstaticmember veri öğesi bir sınıf statik değişkenidir.

DataIsConstant veri öğesi sabit bir değerdir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
