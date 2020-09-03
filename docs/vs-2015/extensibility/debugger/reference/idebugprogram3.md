---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148604"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir işlemde çalışan ve iş parçacığı bilgileri sağlayarak [yürütmeyi](../../../extensibility/debugger/reference/idebugprogram2-execute.md) genişleten bir programı temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası sağlayıcısı, bu arabirimi bir işlem içindeki bir programı temsil etmek için uygular. Oturum hata ayıklama Yöneticisi (SDM), [iliştirilecek](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bilgileri sağlamak için bu arabirimi de uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olayı yeni bir program için bu arabirimi döndürür. Bu arabirim, birden fazla arabirimde birçok yöntem için bir parametre olarak da kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgram3` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Programı yürütür. İş parçacığı, çalıştırıldığında kullanıcı tarafından hangi iş parçacığının görüntülemekte olduğunu hata ayıklayıcı bilgilerini vermek üzere döndürülür.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program, belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısıdır ve bir işlem bir veya daha fazla programdan oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [İleri](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Destroyıprogram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
