---
title: Desteklenen Etkinlik Türleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712808"
---
# <a name="supported-event-types"></a>Desteklenen etkinlik türleri
Visual Studio hata ayıklama şu anda aşağıdaki olay türlerini destekler:

- Eşzamanlı olaylar

   Oturum hata ayıklama yöneticisine (SDM) ve IDE'ye, hata ayıklanan uygulamanın durumunun değiştiğini bildirin. Bu olaylar SDM ve IDE boş zamanlarında işlenir. Olay işlendikten sonra hata ayıklama motoruna (DE) yanıt gönderilmez. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) ve [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) arabirimleri eşzamanlı olaylara örnektir.

- Eşzamanlı olaylar

   SDM ve IDE'ye, debugged olan uygulamanın durumunun değiştiğini bildirin. Bu olaylar ve eşzamanlı olaylar arasındaki tek fark, [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yöntemi ile yanıt gönderilmesidir.

   Bir senkron olay gönderme, IDE olay alır ve işler sonra işleme devam etmek için DE gerekiyorsa yararlıdır.

- Olayları eşzamanlı durdurma veya olayları durdurma

   SDM'ye ve IDE'ye, silinen uygulamanın kodu yürütmeyi durdurduğunu bildirin. [Olay](../../extensibility/debugger/reference/idebugeventcallback2-event.md)yöntemi ile bir durdurma olayı gönderdiğinde, [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametresi gereklidir. Durdurma olayları aşağıdaki yöntemlerden birine yapılan bir çağrı ile devam edilir:

  - [Yürütmek](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Adım](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Devam](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri durdurma olaylarının örnekleridir.

  > [!NOTE]
  > Eşkron durdurma olayları desteklenmez. Bir eşzamanlı durdurma olayı göndermek bir hatadır.

## <a name="discussion"></a>Tartışma
 Olayların gerçek uygulanması DE'nizin tasarımına bağlıdır. Gönderilen her olayın türü, DE'yi tasarlarken ayarlanan özniteliklerine göre belirlenir. Örneğin, bir DE bir [IDebugProgramCreateEvent2'yi](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eşzamanlı bir olay olarak gönderebilirken, diğeri bunu durdurma olayı olarak gönderebilir.

 Aşağıdaki tablo, hangi olayların yanı sıra olay türleri için hangi program ve iş parçacığı parametrelerinin gerekli olduğunu belirtir. Herhangi bir olay senkron olabilir. Hiçbir olayın eşzamanlı olması gerekir.

> [!NOTE]
> Tüm olaylar için [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) arabirimi gereklidir.

|Olay|IDebugProgram2|IDebugThread2|Olayları Durdurma|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Gerekli|Gerekli|Hayır|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|İzin verilmiyor|İzin verilmiyor|Hayır|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|İzin verilmiyor|İzin verilmiyor|Hayır|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Olabilir|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Olabilir|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Olabilir|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Gerekli|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Gerekli|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Gerekli|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Gerekli|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Gerekli|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|IDebugStopCompleteEvent2|Gerekli|Gerekli|Evet|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Gerekli|Gerekli|Evet|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Gerekli|Gerekli|Hayır|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Gerekli|Gerekli|Hayır|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|İzin verildi, ancak gerekli değil|İzin verildi, ancak gerekli değil|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [Etkinlik gönderme](../../extensibility/debugger/sending-events.md)
