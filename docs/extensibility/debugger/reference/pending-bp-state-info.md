---
description: Bir kod konumuna bağlanmaya yönelik bir kesme noktasının durumu hakkında bilgi içerir.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4da8892239740c65e1fcbbe618fa1ea76183e96
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079689"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Bir kod konumuna bağlanmaya yönelik bir kesme noktasının durumu hakkında bilgi içerir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Üyeler
 `state`\
 Bekleyen kesme noktasının durumunu belirten [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) numaralandırmasından bir değer.

 `flags`\
 Kesme noktasının sanallaştırılmadığını belirten [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) numaralandırmasındaki bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, doldurulduğu [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
