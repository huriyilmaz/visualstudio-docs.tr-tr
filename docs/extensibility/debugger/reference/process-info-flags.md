---
title: PROCESS_INFO_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713960"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Bir işlemin özelliklerini açıklar veya belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
İşlemin hata ayıklayan tarafından hata ayıklandığını gösterir. Hata ayıklayıcı [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] olabilir veya başka bir hata ayıklayıcı olabilir, örneğin, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
İşlemin durdurulduğunu gösterir. Yalnızca da `PIFLAG_DEBUGGER_ATTACHED` belirtilirse geçerlidir. Visual Studio 2005 ve sonrası mevcuttur.

`PIFLAG_PROCESS_RUNNING`\
İşlemin çalıştığını gösterir. Yalnızca da `PIFLAG_DEBUGGER_ATTACHED` belirtilirse geçerlidir. Visual Studio 2005 ve sonrası mevcuttur.

## <a name="remarks"></a>Açıklamalar

`Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının üyesi için kullanılır.

Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler

Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
