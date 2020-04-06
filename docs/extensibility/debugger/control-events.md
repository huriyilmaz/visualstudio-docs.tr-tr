---
title: Kontrol Olayları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739091"
---
# <a name="control-events"></a>Olayları kontrol edin
Programınızın kontrollü yürütülmesi sırasında olayları göndermeniz gerekir. Tüm olaylar [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) arabirimi kullanılarak gönderilir ve [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) yöntemini uygulamanızı gerektiren özniteliklere sahiptir.

## <a name="additional-methods"></a>Ek yöntemler
 Bazı olaylar aşağıdaki gibi ek yöntemlerin uygulanmasını gerektirir:

- Hata ayıklama motoru (DE) başlattığında [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabiriminin gönderilmesi, [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) yöntemini uygulamanızı gerektirir.

- Yürütme [denetimi, IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) ve[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimleri gibi denetim olaylarının uygulanmasını gerektirir. **IDebugBreakEvent2** yalnızca asynchronous molaları için gereklidir.

- Fonksiyonlara adım atmak için [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabiriminin ve yöntemlerinin uygulanması gerekiyor.

  Kesme noktalarından kaynaklanan olaylar [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)ve [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) arayüzlerinin yanı sıra [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) yöntemlerinin uygulanmasını gerektirir.

  Eşkron ifade [değerlendirmesi, IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimini ve [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[ve GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) yöntemlerini uygulamanızı gerektirir.

  Senkron olaylar [iDebugEngine2 uygulanmasını gerektirir::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yöntemi.

  Motorunuzun dize stili çıktı yazabilmesi için [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) yöntemini uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme kontrolü ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
