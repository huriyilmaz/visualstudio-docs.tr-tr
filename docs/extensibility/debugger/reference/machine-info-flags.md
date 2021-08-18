---
description: Bir makineyi tanımlamak için kullanılır.
title: MACHINE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FLAGS
helpviewer_keywords:
- MACHINE_INFO_FLAGS enumeration
ms.assetid: 1482095d-9a2e-4ef1-9e14-362c0b85194e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7c6f471a1b238f7773876cbf7fb28aaab8679c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152607"
---
# <a name="machine_info_flags"></a>MACHINE_INFO_FLAGS
Bir makineyi tanımlamak için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FLAGS { 
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001
};
typedef DWORD MACHINE_INFO_FLAGS;
```

```csharp
public enum enum_MACHINE_INFO_FLAGS { 
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001
};
```

## <a name="fields"></a>Alanlar
 `MCIFLAG_TERMINAL_SERVICES_AVAILABLE`\
 Terminal hizmetlerinin kullanılabilir olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 MACHINE_INFO `Flags` üyesi [olarak](../../../extensibility/debugger/reference/machine-info.md) kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
