---
description: Bir veri değerinin belirli kapsamını gösterir.
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fbf8d7f40f1cd3c14bd6b830a65526921f1c6ece
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630651"
---
# <a name="datakind"></a>DataKind
Bir veri değerinin belirli kapsamını gösterir.

## <a name="syntax"></a>Syntax

```C++
enum DataKind {
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
DataIsUnknown Veri simgesi belirlenemez.

DataIsLocal Data öğesi yerel bir değişkendir.

DataIsStaticLocal Veri öğesi statik bir yerel değişkendir.

DataIsParam Veri öğesi resmi bir parametredir.

DataIsObjectPtr Veri öğesi bir nesne işaretçisidir ( `this` ).

DataIsFileStatic Data öğesi, dosya kapsamlı bir değişkendir.

DataIsGlobal Data öğesi genel bir değişkendir.

DataIsMember Data öğesi bir nesne üyesi değişkenidir.

DataIsStaticMember Veri öğesi bir sınıf statik değişkenidir.

DataIsConstant Veri öğesi sabit bir değerdir.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_dataKind yöntemi tarafından](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
