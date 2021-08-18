---
description: Bir programın durumunun ne kadarının (iş parçacıkları, yığın çerçeveleri ve geçerli yönerge adresi gibi) dökümünü belirtir.
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10815aece24f5fd95990a71406322b5de2b634ee1a82568dd622db9edbbfd1fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452347"
---
# <a name="dumptype"></a>DUMPTYPE
Bir programın durumunun ne kadarının (iş parçacıkları, yığın çerçeveleri ve geçerli yönerge adresi gibi) dökümünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Alanlar
`DUMP_MINIDUMP`\
Küçük, kompakt bir döküm belirtir.

`DUMP_FULLDUMP`\
Büyük ve tamamlanmış bir döküm belirtir.

## <a name="remarks"></a>Açıklamalar
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
