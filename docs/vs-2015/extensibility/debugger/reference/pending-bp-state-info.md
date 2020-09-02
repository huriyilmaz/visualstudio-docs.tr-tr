---
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af22ef2d8a77b8c44b9e494736630480a0614162
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205066"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir kod konumuna bağlanmaya yönelik bir kesme noktasının durumu hakkında bilgi içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 state  
 Bekleyen kesme noktasının durumunu belirten [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) numaralandırmasından bir değer.  
  
 bayraklar  
 Kesme noktasının sanallaştırılmadığını belirten [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) numaralandırmasındaki bayrakların birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, doldurulduğu [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) yöntemine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
