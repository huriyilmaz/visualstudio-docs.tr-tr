---
description: Erişilen bellek türünü belirtir.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5dd391950b3f5441d9f6d2b4e6030abfa5a399b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121167"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Erişilen bellek türünü belirtir.

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
`MemTypeCode` Yalnızca kod belleğine erişer.

`MemTypeData` Verilere veya yığın belleğine erişer.

`MemTypeStack` Yalnızca yığın belleğine erişer.

`MemTypeAny` Her türlü belleğe erişer.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler, farklı bellek türlerine erişimi sınırlamak için [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
