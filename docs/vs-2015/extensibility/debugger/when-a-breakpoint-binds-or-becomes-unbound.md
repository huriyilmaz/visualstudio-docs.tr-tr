---
title: Bir kesme noktası bağlandığında veya Ilişkisiz hale geldiğinde | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1425edc2c8fc3fe8c38c133388f90b18b516b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162171"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Kesme Noktasının Bağlandığı veya Bağlanmamış Hale Geldiği Durumlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kesme noktası, [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) yöntemine bir çağrı yapıldığında bağlama sırasında bağlantı noktası ve oluşturma süresi farklıdır.  
  
## <a name="methods-called"></a>Çağrılan Yöntemler  
 Oturum hata ayıklama Yöneticisi (SDM) aşağıdaki yöntemleri çağırır:  
  
1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)döndürür.  
  
2. [IDebugPendingBreakpoint2:: Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3. [IDebugPendingBreakpoint2:: Sanallaştır](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4. [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi ve s_ok döndürür. DE bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) veya [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)gönderir.  
  
5. [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) yöntemlerini doğrulamak ve bu noktaları almak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
