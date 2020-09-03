---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2cd255ab59c9d46676ba46baddd9cee7e3ef4cc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461184"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Erişmek için bellek türünü belirtir.

## <a name="syntax"></a>Söz dizimi

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parametreler
`MemTypeCode` Yalnızca kod belleğine erişir.

`MemTypeData` Verilere veya yığın belleğine erişir.

`MemTypeStack` Yalnızca yığın belleğine erişir.

`MemTypeAny` Her türlü belleğe erişir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, farklı bellek türlerine erişimi sınırlandırmak için [IDiaStackWalkHelper:: readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
