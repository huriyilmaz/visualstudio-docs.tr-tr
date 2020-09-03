---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad36363ff20e285dde2db6fc723ddf2562c491f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156171"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir kod konumuna bağlanan bir kesme noktasını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) çağrısı bu arabirimi oluşturur. [Getbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) ve [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) çağrıları da bu arabirimi alabilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBoundBreakpoint2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Belirtilen bağlantılı kesme noktasının oluşturulduğu bekleyen kesme noktasını alır.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bu bağlantılı kesme noktasının durumunu alır.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Bu bağlantılı kesme noktası için geçerli isabet sayısını alır.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Bu kesme noktasını açıklayan kesme noktası çözünürlüğünü alır.|  
|[Etkinleştirme](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Kesme noktasını etkinleştirilir veya devre dışı bırakır.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Bu bağlantılı kesme noktası için isabet sayısını ayarlar.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Bu ilişkili kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Bu ilişkili kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.|  
|[Silme](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Kesme noktasını siler.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [İleri](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
