---
title: PENDING_BP_STATE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69c8dbe1022ee0b1b2ff034d2b83b947c8fb3df6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714003"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Bekleyen bir kesme noktasının durumunu (henüz bağlanmamış bir kesme noktası) belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Alanlar
 `PBPS_NONE`\
 Yer tutucu sıfır. Bu değer hiçbir zaman döndürülür.

 `PBPS_DELETED`\
 Bekleyen kesme noktasının silindiğini gösterir.

 `PBPS_DISABLED`\
 Bekleyen kesme noktasının devre dışı bırakıldığını gösterir.

 `PBPS_ENABLED`\
 Bekleyen kesme noktasının etkin olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 `state` [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) yapının üyesi olarak kullanın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
