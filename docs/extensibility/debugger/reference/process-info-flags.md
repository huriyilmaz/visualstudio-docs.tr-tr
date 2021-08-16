---
description: Bir işlemin özelliklerini açıklar veya belirtir.
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1b72ade6d2cdc93ed3cb60ff5feba8589268f1b540692b5a9e8b3802ec31e89
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377307"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Bir işlemin özelliklerini açıklar veya belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Alanlar

`PIFLAG_SYSTEM_PROCESS`\
İşlemin bir sistem işlemi olduğunu gösterir.

`PIFLAG_DEBUGGER_ATTACHED`\
İşlemin hata ayıklayıcı tarafından ayıklanmakta olduğunu gösterir. Bu bir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı olabilir ya da başka bir hata ayıklayıcı (örneğin, WinDbg) olabilir.

`PIFLAG_PROCESS_STOPPED`\
İşlemin durdurulduğunu belirtir. Yalnızca `PIFLAG_DEBUGGER_ATTACHED` Ayrıca belirtilmişse geçerlidir. Visual Studio 2005 ve üzeri sürümlerde kullanılabilir.

`PIFLAG_PROCESS_RUNNING`\
İşlemin çalıştığını gösterir. Yalnızca `PIFLAG_DEBUGGER_ATTACHED` Ayrıca belirtilmişse geçerlidir. Visual Studio 2005 ve üzeri sürümlerde kullanılabilir.

## <a name="remarks"></a>Açıklamalar

`Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının üyesi için kullanılır.

Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler

Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
