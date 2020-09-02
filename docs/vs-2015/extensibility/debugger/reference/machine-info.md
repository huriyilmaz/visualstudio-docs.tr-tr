---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac571a1e1c7a9d6cff1caaca40f1c6568f99adf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546794"
---
# <a name="machine_info"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirli bir makineyi açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 `Fields`  
 Yapının hangi alanlarının başlatıldığını belirten [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Numaralandırmadaki bayrakların birleşimi.  
  
 `bstrName`  
 Makine adı. [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)çağırma ile eşdeğerdir.  
  
 `Flags`  
 Makine özniteliklerini açıklayan [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) Numaralandırmadaki bayrakların birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı [Getmachineınfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) yöntemine yapılan bir çağrı ile döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
