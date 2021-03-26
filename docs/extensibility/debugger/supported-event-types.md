---
title: Desteklenen olay türleri | Microsoft Docs
description: Zaman uyumsuz olaylar, zaman uyumlu olaylar ve durdurma olayları dahil olmak üzere Visual Studio hata ayıklamanın desteklediği olay türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 883c9fd51cc4dfc4f2cc2f996d24c0722478505f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079416"
---
# <a name="supported-event-types"></a>Desteklenen olay türleri
Visual Studio hata ayıklaması Şu anda aşağıdaki olay türlerini destekler:

- Zaman uyumsuz olaylar

   Hata ayıklama Yöneticisi (SDM) ve IDE 'ye, hata ayıklamakta olan uygulamanın durumunun değişmekte olduğunu bildirin. Bu olaylar, SDM ve IDE 'nin boş olarak işlenir. Olay işlendikten sonra hata ayıklama altyapısına (DE) yanıt gönderilmez. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) ve [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) arabirimleri, zaman uyumsuz olay örnekleridir.

- Zaman uyumlu olaylar

   Hata ayıklamakta olan uygulamanın durumunun değişmekte olduğunu SDM ve IDE 'ye bildirin. Bu olaylar ve zaman uyumsuz olaylar arasındaki tek fark, [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yöntemi tarafından bir yanıtın gönderilmesi anlamına gelir.

   Bir zaman uyumlu olay gönderilmesi, IDE 'nin olayı aldıktan ve işledikten sonra işlemeye devam etmesi gerekiyorsa yararlıdır.

- Zaman uyumlu durdurma olayları veya olayları durduruluyor

   SDM 'ye ve hata ayıklamakta olan uygulamanın kod yürütmeyi durdurdu olduğunu bildirin. Yöntem [olayı](../../extensibility/debugger/reference/idebugeventcallback2-event.md)aracılığıyla bir durdurma olayı gönderdiğinizde, [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametresi gereklidir. Olayları durdurma aşağıdaki yöntemlerden birine yapılan bir çağrı ile devam eder:

  - [Yürütme](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Adım](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Devam et](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri, olayları durdurma örnekleridir.

  > [!NOTE]
  > Zaman uyumsuz durdurma olayları desteklenmez. Zaman uyumsuz durdurma olayı gönderilmesi hatadır.

## <a name="discussion"></a>Tartışma
 Olayların gerçek uygulanması, ve ' in tasarımına bağlıdır. Gönderilen her olayın türü, DE ' yi tasarlarken ayarlanan özniteliklerine göre belirlenir. Örneğin, bir aynı zaman uyumsuz bir olay olarak bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gönderebilir, başka bir durum da durdurma olayı olarak gönderebilir.

 Aşağıdaki tabloda hangi programın ve iş parçacığı parametrelerinin hangi olayların yanı sıra olay türleri için gerekli olduğu belirtilir. Herhangi bir olay zaman uyumlu olabilir. Zaman uyumlu olması gereken olay yok.

> [!NOTE]
> Tüm olaylar için [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) arabirimi gereklidir.

|Olay|IDebugProgram2|IDebugThread2|Olayları durdurma|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Gerekli|Gerekli|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|İzin verilmiyor|İzin verilmiyor|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|İzin verilmiyor|İzin verilmiyor|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|Olabilir|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|Olabilir|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|Olabilir|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Gerekli|İzin veriliyor, ancak gerekli değil|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Gerekli|İzin veriliyor, ancak gerekli değil|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Gerekli|İzin veriliyor, ancak gerekli değil|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Gerekli|İzin veriliyor, ancak gerekli değil|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Gerekli|İzin veriliyor, ancak gerekli değil|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|IDebugStopCompleteEvent2|Gerekli|Gerekli|Yes|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Gerekli|Gerekli|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Gerekli|Gerekli|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|İzin veriliyor, ancak gerekli değil|İzin veriliyor, ancak gerekli değil|No|

## <a name="see-also"></a>Ayrıca bkz.
- [Olayları gönderme](../../extensibility/debugger/sending-events.md)
