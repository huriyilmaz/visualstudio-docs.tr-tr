---
description: Bekleyen bir kesme noktası (henüz bağlı değil bir kesme noktası) durumunu belirtir.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 191d73dcf5b4e1f7b0e3b10842d9a6806a95e9c2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726973"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Bekleyen bir kesme noktası (henüz bağlı değil bir kesme noktası) durumunu belirtir.

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
 Sıfır için yer tutucu. Bu değer hiçbir zaman döndürülz.

 `PBPS_DELETED`\
 Bekleyen kesme noktası silindi gösterir.

 `PBPS_DISABLED`\
 Bekleyen kesme noktası devre dışı olduğunu gösterir.

 `PBPS_ENABLED`\
 Bekleyen kesme noktası etkin olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 Bu `state` yapının üyesi olarak [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
