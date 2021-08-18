---
title: Olayları Denetleme | Microsoft Docs
description: IDebugEvent2 arabirimini kullanarak programınızı denetimli yürütme sırasında olay gönderme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7ca8f78172613a41a6864490bedd99fc1f32393c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111781"
---
# <a name="control-events"></a>Olayları denetleme
Programınız denetlenen yürütme sırasında olayları göndermeniz gerekir. Tüm olaylar [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) arabirimi kullanılarak gönderilir ve [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) yöntemini uygulamanız gereken özniteliklere sahiptir.

## <a name="additional-methods"></a>Ek yöntemler
 Bazı olaylar aşağıdaki gibi ek yöntemlerin uygulanmasını gerektirir:

- Hata ayıklama altyapısı (DE) başlatılmışken [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabirimini göndermek [için IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) yöntemini uygulamamız gerekir.

- Yürütme denetimi, [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) ve[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimleri gibi denetim olaylarının uygulanmasını gerektirir. **IDebugBreakEvent2** yalnızca zaman uyumsuz kesmeler için gereklidir.

- İşlevlere adımlama, [IDebugStepCompleteEvent2 arabiriminin](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) ve yöntemlerinin uygulanmasını gerektirir.

  Kesme noktalarından türetilmiş olaylar [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)ve [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) arabirimlerinin yanı sıra [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ve [EnumBoundBreakpoint yöntemlerinin](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) uygulanmasını gerektirir.

  Zaman uyumsuz ifade değerlendirmesi [için IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimini ve [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)ve[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) yöntemlerini uygulama gerekir.

  Zaman uyumlu [olaylar, IDebugEngine2::ContinueFromSynchronousEvent yönteminin uygulanmasını](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) gerektirir.

  Altyapınız dize stilinde çıkış yazacaksa [IDebugOutputStringEvent2::GetString yöntemini uygulamanız](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
