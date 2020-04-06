---
title: Kırılma Noktası Ile İlgili Yöntemler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739200"
---
# <a name="breakpoint-related-methods"></a>Kesme noktası ile ilgili yöntemler
Hata ayıklama altyapısı (DE) kesme noktalarıayarını desteklemelidir. Visual Studio hata ayıklama aşağıdaki kesme noktaları türlerini destekler:

- Bound

     UI üzerinden istenen ve belirli bir kod konumuna başarıyla bağlı

- Beklemede

     UI üzerinden istenen ancak henüz gerçek talimatlara bağlı değil

## <a name="discussion"></a>Tartışma
 Örneğin, bekleyen bir kesme noktası, yönergeler henüz yüklenmediğinde oluşur. Kod yüklendiğinde, bekleyen kesme noktaları koda kesme yönergeleri eklemek için öngörülen konumdaki koda bağlamaya çalışır. Olaylar, başarılı bağlamayı belirtmek veya bağlama hataları olduğunu bildirmek için oturum hata ayıklama yöneticisine (SDM) gönderilir.

 Bekleyen bir kesme noktası, karşılık gelen bağlı kesme noktalarının kendi iç listesini de yönetir. Bekleyen bir kesme noktası, koda birçok kesme noktası eklenmesine neden olabilir. Visual Studio hata ayıklama UI bekleyen kesme noktaları ve karşılık gelen bağlı kesme noktaları bir ağaç görünümünü gösterir.

 Bekleyen kesme noktalarının oluşturulması ve kullanılması [iDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yönteminin yanı sıra [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimlerinin aşağıdaki yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bekleyen bir kesme noktasının kod konumuna bağlanıp bağlanamayacağını belirler.|
|[Bağla](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bekleyen bir kesme noktasını bir veya daha fazla kod konumuna bağlar.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bekleyen bir kesme noktası nın durumunu alır.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bekleyen bir kesme noktası oluşturmak için kullanılan kesme noktası isteğini alır.|
|[Etkinleştir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bekleyen bir kesme noktasının etkin durumunu geçişe erdirin.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bekleyen bir kesme noktasından bağlı tüm kesme noktalarını olur.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bekleyen bir kesme noktasından kaynaklanan tüm hata kesme noktalarını doğrular.|
|[Sil](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bekleyen bir kesme noktasını ve ondan bağlanan tüm kesme noktalarını siler.|

 Bağlı kesme noktalarını ve hata kesme noktalarını sayısallandırmak için [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) ve [IEnumDebugErrorBreakpoints2'nin](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)tüm yöntemlerini uygulamanız gerekir.

 Kod konumuna bağlanan bekleyen kesme noktaları, aşağıdaki [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Kesme noktası içeren bekleyen kesme noktasını alır.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bağlı bir kesme noktasının durumunu alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Kesme noktası açıklayan kesme noktası çözümünü alır.|
|[Etkinleştir](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Kesme noktasını etkinleştirir veya devre dışı kılabilir.|
|[Sil](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Bağlı bir kesme noktasını siler.|

 Çözüm ve istek bilgileri, aşağıdaki [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Bir çözümle temsil edilen kesme noktasının türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Kesme noktası açıklayan kesme noktası çözümleme bilgilerini alır.|

 Bağlama sırasında oluşabilecek hataların çözümü için aşağıdaki [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) yöntemlerinin uygulanması nı gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Hata kesme noktası içeren bekleyen kesme noktasını alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Bir hata kesme noktası açıklayan kesme noktası hata çözümünü alır.|

 Bağlama sırasında oluşabilecek hataların çözümü de [iDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)aşağıdaki yöntemleri gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Bir kırılma noktası türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Kesme noktasının çözüm bilgilerini alır.|

 Bir kesme noktasında kaynak kodu görüntüleme [IDebugStackFrame2 yöntemlerini uygulamak için gerektirir::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve / veya [IDebugStackFrame2 yöntemleri::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme kontrolü ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
