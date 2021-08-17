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
ms.openlocfilehash: 891af8c8f6196fcafa8f623fa0fd81c44548b81c9a3294001312c2a7c6e341d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420377"
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
