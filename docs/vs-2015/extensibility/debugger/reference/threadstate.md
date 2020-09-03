---
title: THREADSTATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e2f6e8011b001c88743871a137ebc0b8cd7c26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204790"
---
# <a name="threadstate"></a>THREADSTATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İş parçacığının durumunu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Üyeler  
 THREADSTATE_RUNNING  
 İş parçacığının çalıştığını gösterir.  
  
 THREADSTATE_STOPPED  
 Bir kesme noktası nedeniyle iş parçacığının durdurulduğunu belirtir.  
  
 THREADSTATE_FRESH  
 İş parçacığının oluşturulduğunu, ancak henüz kod çalışmadığını gösterir.  
  
 THREADSTATE_DEAD  
 İş parçacığının ölü olduğunu gösterir.  
  
 THREADSTATE_FROZEN  
 İş parçacığının dondurulmuş olduğunu belirtir (yürütme yapılamaz).  
  
## <a name="remarks"></a>Açıklamalar  
 `dwThreadState` [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) yapısının alanı için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
