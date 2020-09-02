---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205060"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir işlemin özelliklerini açıklar veya belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
## <a name="members"></a>Üyeler  
 PIFLAG_SYSTEM_PROCESS  
 İşlemin bir sistem işlemi olduğunu gösterir.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 İşlemin hata ayıklayıcı tarafından ayıklanmakta olduğunu gösterir. Bu bir [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklayıcı olabilir ya da başka bir hata ayıklayıcı (örneğin, WinDbg) olabilir.  
  
 PIFLAG_PROCESS_STOPPED  
 İşlemin durdurulduğunu belirtir. Yalnızca `PIFLAG_DEBUGGER_ATTACHED` Ayrıca belirtilmişse geçerlidir. [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]Ve sonraki sürümlerinde kullanılabilir.  
  
 PIFLAG_PROCESS_RUNNING  
 İşlemin çalıştığını gösterir. Yalnızca `PIFLAG_DEBUGGER_ATTACHED` Ayrıca belirtilmişse geçerlidir. [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]Ve sonraki sürümlerinde kullanılabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının üyesi için kullanılır.  
  
 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
