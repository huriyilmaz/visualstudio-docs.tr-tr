---
title: Desteklenen Olay Türleri | Microsoft Docs
description: Zaman uyumsuz olaylar, zaman uyumlu olaylar Visual Studio durdurma olayları da dahil olmak üzere hata ayıklamanın desteklediği olay türleri hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ce77f01c2cae0e1f56b9a55b41f291dc7814a2b5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626426"
---
# <a name="supported-event-types"></a>Desteklenen olay türleri
Visual Studio hata ayıklama şu anda aşağıdaki olay türlerini destekler:

- Zaman uyumsuz olaylar

   Oturum hata ayıklama yöneticisine (SDM) ve IDE'ye, hata ayıklama yapılan uygulamanın durumunun değişmektedir. Bu olaylar SDM ve IDE'nin hemen ardından işlenir. Olay işlendikten sonra hata ayıklama altyapısına (DE) yanıt gönderilmez. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) ve [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) arabirimleri, zaman uyumsuz olaylara örnektir.

- Zaman uyumlu olaylar

   SDM ve IDE'ye hata ayıklama yapılan uygulamanın durumunun değişte olduğunu bildirin. Bu olaylarla zaman uyumsuz olaylar arasındaki tek fark [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yöntemiyle bir yanıtın gönderilmiş olmasıdır.

   IDE olayı aldığında ve işledikten sonra işlemeye devam etmek için DE'nize ihtiyacınız varsa zaman uyumlu bir olay göndermek yararlı olur.

- Zaman uyumlu durdurma olayları veya olayları durdurma

   SDM'ye ve IDE'ye hata ayıklan uygulamanın kodu yürütmeyi durdurmuş olduğunu bildirme. Event yöntemiyle bir durdurma olayı [gönderirken](../../extensibility/debugger/reference/idebugeventcallback2-event.md) [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametresi gereklidir. Durdurma olayları aşağıdaki yöntemlerden birinin çağrısıyla devam eder:

  - [Yürütme](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Adım](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Devam et](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri, olayları durdurma örnekleridir.

  > [!NOTE]
  > Zaman uyumsuz durdurma olayları desteklenmiyor. Zaman uyumsuz durdurma olayı göndermek bir hatadır.

## <a name="discussion"></a>Tartışma
 Olayların gerçek uygulaması, DE'nizin tasarımına bağlıdır. Gönderilen her olayın türü, DE'i tasarlarken ayarlanmış öznitelikleri tarafından belirlenir. Örneğin, bir DE bir [IDebugProgramCreateEvent2'i](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zaman uyumsuz bir olay olarak, diğeri de durdurma olayı olarak gönderebilir.

 Aşağıdaki tabloda hangi program ve iş parçacığı parametrelerinin hangi olaylar için gerekli olduğu ve olay türleri belirtmektedir. Herhangi bir olay zaman uyumlu olabilir. Hiçbir olayın zaman uyumlu olması gerek yoktur.

> [!NOTE]
> [IDebugEngine2 arabirimi](../../extensibility/debugger/reference/idebugengine2.md) tüm olaylar için gereklidir.

|Olay|IDebugProgram2|IDebugThread2|Olayları Durdurma|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Gerekli|Gerekli|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|İzin verilmiyor|İzin verilmiyor|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|İzin verilmiyor|İzin verilmiyor|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|Şu olabilir:|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|Şu olabilir:|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|Şu olabilir:|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Gerekli|İzin verildi ama gerekli değil|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Gerekli|İzin verildi ama gerekli değil|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Gerekli|İzin verildi ama gerekli değil|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Gerekli|İzin verildi ama gerekli değil|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Gerekli|İzin verildi ama gerekli değil|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|IDebugStopCompleteEvent2|Gerekli|Gerekli|Yes|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Gerekli|Gerekli|Yes|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Gerekli|Gerekli|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Gerekli|Gerekli|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|İzin verildi ama gerekli değil|İzin verildi ama gerekli değil|No|

## <a name="see-also"></a>Ayrıca bkz.
- [Olayları gönderme](../../extensibility/debugger/sending-events.md)
