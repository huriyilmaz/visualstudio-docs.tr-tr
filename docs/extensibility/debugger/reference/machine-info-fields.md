---
description: Belirli bir makine için alınacak bilgi türünü belirtir.
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3361ed090dc724f948d98aa0037949e0c573d56d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057942"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Belirli bir makine için alınacak bilgi türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Alanlar
 `MCIF_NAME`\
 Yapıda alanı başlatın/kullanın `bstrName` .

 `MCIF_FLAGS`\
 Yapıda alanı başlatın/kullanın `Flags` .

 `MIF_ALL`\
 Yapıdaki tüm alanları başlatın/kullanın.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) yapısının hangi üyelerinin başlatıldığını göstermek Için [getmachineınfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) yöntemine geçirilir.

 Ayrıca, `Fields` `MACHINE_INFO` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapının üyesinde de kullanılır.

 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
