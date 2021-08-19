---
description: Belirli bir makineyi açıklar.
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e230937de42ebda2697fe4cc43fc77bbee340cfb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125380"
---
# <a name="machine_info"></a>MACHINE_INFO
Belirli bir makineyi açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>Üyeler
 `Fields`\
 Yapının hangi [alanlarının başlat MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) bir numaralandırılan bayrakların birleşimi.

 `bstrName`\
 Makine adı. [GetMachineName çağrısına eşdeğerdir.](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)

 `Flags`\
 Makine özniteliklerini açıklayan [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [GetMachineInfo yöntemine yapılan bir çağrıyla](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
