---
title: Bir kesme noktası bağlandığında veya Ilişkisiz hale geldiğinde | Microsoft Docs
description: İlişkisiz kesme noktaları hakkında bilgi edinin. Bir kesme noktası bir çağrı yapıldığında bağlanamaz, kesme noktasının bağlama süresi ve oluşturma saati farklıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a2373497f56f1c689de12bdd72e55fba84f51cc5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626313"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Bir kesme noktası bağlandığında veya bağlantısı kesilirse
Bir kesme noktası, [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) yöntemine bir çağrı yapıldığında bağlama sırasında bağlantı noktası ve oluşturma süresi farklıdır.

## <a name="methods-called"></a>Çağrılan Yöntemler
 Oturum hata ayıklama Yöneticisi (SDM) aşağıdaki yöntemleri çağırır:

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)döndürür.

2. [IDebugPendingBreakpoint2:: Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: Sanallaştır](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi ve s_ok döndürür. DE bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) veya [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)gönderir.

5. [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) yöntemlerini doğrulamak ve bu noktaları almak için.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
