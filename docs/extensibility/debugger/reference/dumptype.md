---
title: DÖKÜM TÜRÜ | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d4d42709efdefe097b4c8a78a0b00f45f2e1a2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737207"
---
# <a name="dumptype"></a>DUMPTYPE
Bir programın durumunun ne kadarının (çalışan iş parçacıkları, yığın çerçeveleri ve geçerli yönerge adresi gibi) ne kadarının çöpe atılmasını belirtir.

## <a name="syntax"></a>Sözdizimi

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
Büyük, tam bir dökümü belirtir.

## <a name="remarks"></a>Açıklamalar
[Yazma Dökümü](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) yöntemine bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
