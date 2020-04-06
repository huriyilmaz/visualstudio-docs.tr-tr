---
title: Bir Breakpoint Bağlanır veya Unbound olur | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712340"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Bir kesme noktası bağlandığında veya bağlanmadığında
Bir kesme noktası [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) yöntemine bir çağrı yapıldığı anda bağlanamadığınızda, bağlama süresi ve kesme noktasının zamanını oluşturma farklıdır.

## <a name="methods-called"></a>Denilen yöntemler
 Oturum hata ayıklama yöneticisi (SDM) aşağıdaki yöntemleri çağırır:

1. [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)döndürür.

2. [IDebugPendingBreakpoint2::Etkinleştir.](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

3. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. [IDebugPendingBreakpoint2::Bağlama](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi ve S_OK döndürür. DE bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) veya [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)gönderir.

5. [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) yöntemleri doğrulamak ve bağlı kesme noktaları almak için.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
