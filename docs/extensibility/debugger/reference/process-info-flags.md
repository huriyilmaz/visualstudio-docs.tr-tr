---
description: Bir işlem özelliklerini açıklar veya belirtir.
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
ms.openlocfilehash: c2708f2cdf4d2bb9150eaf1b5f235ddecc4164e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050539"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Bir işlem özelliklerini açıklar veya belirtir.

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
sürecin bir sistem işlemi olduğunu gösterir.

`PIFLAG_DEBUGGER_ATTACHED`\
Bir hata ayıklayıcı tarafından işlemde hata ayıklandı olduğunu gösterir. Bu bir hata ayıklayıcısı veya winDbg gibi başka bir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı olabilir.

`PIFLAG_PROCESS_STOPPED`\
sürecin durdurulmuş olduğunu gösterir. Yalnızca aynı zamanda `PIFLAG_DEBUGGER_ATTACHED` belirtilmişse geçerlidir. 2005 Visual Studio sonraki bir yıl içinde kullanılabilir.

`PIFLAG_PROCESS_RUNNING`\
İşlem çalışıyor olduğunu gösterir. Yalnızca aynı zamanda `PIFLAG_DEBUGGER_ATTACHED` belirtilmişse geçerlidir. 2005 Visual Studio sonraki bir yıl içinde kullanılabilir.

## <a name="remarks"></a>Açıklamalar

Bu `Flags` yapının üyesi [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) kullanılır.

Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler

Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
