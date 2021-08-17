---
description: Bir programın durumunun ne kadarını (örneğin, çalışan iş parçacıkları, yığın çerçeveleri ve geçerli yönerge adresi) döküm olarak belirtir.
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
ms.openlocfilehash: 3054d86c1d516f79cbf259eaaf4add7ae1befc51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104631"
---
# <a name="dumptype"></a>DUMPTYPE
Bir programın durumunun ne kadarını (örneğin, çalışan iş parçacıkları, yığın çerçeveleri ve geçerli yönerge adresi) döküm olarak belirtir.

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
Küçük, sıkıştırılmış bir döküm belirtir.

`DUMP_FULLDUMP`\
Büyük ve eksiksiz bir döküm belirtir.

## <a name="remarks"></a>Açıklamalar
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) yöntemine bağımsız değişken olarak geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
