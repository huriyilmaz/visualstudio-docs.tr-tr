---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738629"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Erişmek için bellek türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parametreler
`MemTypeCode` yalnızca kod belleğine erişir.

`MemTypeData` veriye veya yığın belleğine erişir.

`MemTypeStack` yalnızca yığın belleğine erişir.

`MemTypeAny` her türlü belleğe erişir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, farklı bellek türlerine erişimi sınırlandırmak için [IDiaStackWalkHelper:: readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
