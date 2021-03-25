---
description: Bekleyen bir kesme noktasının durumunu belirtir (henüz bağlanmamış bir kesme noktası).
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d041042be92fe68dd6f0ea35bbdb4f6dd6d9ac7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086384"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Bekleyen bir kesme noktasının durumunu belirtir (henüz bağlanmamış bir kesme noktası).

## <a name="syntax"></a>Syntax

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Alanlar
 `PBPS_NONE`\
 Sıfır için yer tutucu. Bu değer hiçbir şekilde döndürülmez.

 `PBPS_DELETED`\
 Bekleyen kesme noktasının silindiğini gösterir.

 `PBPS_DISABLED`\
 Bekleyen kesme noktasının devre dışı olduğunu belirtir.

 `PBPS_ENABLED`\
 Bekleyen kesme noktasının etkin olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 `state` [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) yapısının üyesi olarak kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
