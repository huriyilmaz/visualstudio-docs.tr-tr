---
title: Denetim olayları | Microsoft Docs
description: IDebugEvent2 arabirimini kullanarak programınızın denetlenen yürütmesi sırasında olayları gönderme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aeee5ed91eca7666d08dfd08ec02b850a7739db9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085539"
---
# <a name="control-events"></a>Denetim olayları
Programınızın denetlenen yürütmesi sırasında olayları göndermeniz gerekir. Tüm olaylar [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) arabirimi kullanılarak gönderilir ve [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodunu uygulamanızı gerektiren özniteliklere sahiptir.

## <a name="additional-methods"></a>Ek Yöntemler
 Bazı olaylar, aşağıdaki gibi ek yöntemlerin uygulanmasını gerektirir:

- Hata ayıklama altyapısı (DE) başlatıldığında [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabirimini göndermek, [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) metodunu uygulamanızı gerektirir.

- Yürütme denetimi, [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) ve[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimleri olarak bu tür denetim olaylarının uygulanmasını gerektirir. **IDebugBreakEvent2** yalnızca zaman uyumsuz kesmeler için gereklidir.

- İşlevlere adımlamak için [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimi ve yöntemlerinin uygulanması gerekir.

  Kesme noktalarından türetilen olaylar, [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) yöntemlerinin yanı sıra [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)ve [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) arabirimlerinin uygulanmasını gerektirir.

  Zaman uyumsuz ifade değerlendirmesi için [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimini ve [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[ve GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) yöntemlerini uygulamanız gerekir.

  Zaman uyumlu olaylar, [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yönteminin uygulanmasını gerektirir.

  Altyapınız dize stili çıkış yazmak için [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metodunu uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
