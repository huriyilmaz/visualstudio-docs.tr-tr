---
title: Breakpoint-Related Yöntemleri | Microsoft Docs
description: Visual Studio hata ayıklaması, kodda bir konuma başarıyla bağlı olan bağlı kesme noktaları ve henüz bağlı olan bekleyen kesme noktaları destekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ad634ddce8f42c8bf5e183ebdf8f75389553dba5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073441"
---
# <a name="breakpoint-related-methods"></a>Kesme noktasıyla ilgili yöntemler
Hata ayıklama altyapısı (DE), kesme noktası ayarını desteklemeli. Visual Studio hata ayıklama aşağıdaki kesme noktası türlerini destekler:

- Bound

     Kullanıcı arabirimi üzerinden istenen ve belirtilen kod konumunu başarıyla bağlı olan

- Beklemede

     Kullanıcı arabirimi üzerinden istenen ancak henüz gerçek yönergelere bağlı değil

## <a name="discussion"></a>Tartışma
 Örneğin, yönergeler henüz yüklenmemişse bekleyen bir kesme noktası oluşur. Kod yüklendiğinde bekleyen kesme noktaları, koda kesme yönergeleri eklemek için koda önceden verilen konumda bağlamayı dener. Olaylar, bağlamanın başarılı olduğunu göstermek veya bağlama hataları olduğunu bildirmek için oturum hata ayıklama yöneticisine (SDM) gönderilir.

 Bekleyen bir kesme noktası, karşılık gelen bağlı kesme noktalarına ait kendi iç listesini de yönetir. Bekleyen bir kesme noktası, koda birçok kesme noktası eklemeye neden olabilir. Hata Visual Studio arabiriminde bekleyen kesme noktaları ve buna karşılık gelen sınır kesme noktaları ağaç görünümü gösterir.

 Bekleyen kesme noktaları oluşturma ve kullanma, [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yönteminin ve aşağıdaki [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimlerinin yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Belirtilen bir bekleyen kesme noktasıyla kod konumunun bağlanıp bağlanamayacağını belirler.|
|[Bağlamak](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Belirtilen bekleyen kesme noktası bir veya daha fazla kod konumunu bağlar.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bekleyen bir kesme noktası durumunu alır.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bekleyen bir kesme noktası oluşturmak için kullanılan kesme noktası isteğini alır.|
|[Etkinleştirme](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Beklemedeki bir kesme noktası için etkin durumu iki durumlu olarak gösterir.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bekleyen bir kesme noktasıyla bağlı olan tüm kesme noktaları numaralarını gösterir.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bekleyen bir kesme noktası sonucunda ortaya çıkan tüm hata kesme noktaları numaralandır.|
|[Silme](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bekleyen bir kesme noktası ve buna bağlı tüm kesme noktaları silinir.|

 Bağlı kesme noktaları ve hata kesme noktaları için [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) ve [IEnumDebugErrorBreakpoints2'nin](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)tüm yöntemlerini uygulamalısınız.

 Bir kod konuma bağlı bekleyen kesme noktaları aşağıdaki [IDebugBoundBreakpoint2 yöntemlerinin uygulanmasını](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Kesme noktası içeren bekleyen kesme noktası alır.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bağlı bir kesme noktası durumunu alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Bir kesme noktası açıklayan kesme noktası çözümlemesi alır.|
|[Etkinleştirme](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Kesme noktası etkinleştirme veya devre dışı bırakma.|
|[Silme](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Bağlı bir kesme noktası siler.|

 Çözüm ve istek bilgileri için aşağıdaki [IDebugBreakpointResolution2 yöntemlerinin uygulanması](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Çözümlemeyle temsil edilen kesme noktası türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktası açıklayan kesme noktası çözümleme bilgilerini alır.|

 Bağlama sırasında ortaya çıkabilir hataların çözümü için aşağıdaki [IDebugErrorBreakpoint2 yöntemlerinin uygulanması](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Hata kesme noktası içeren bekleyen kesme noktası alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Bir hata kesme noktası açıklayan kesme noktası hata çözümlemesi alır.|

 Bağlama sırasında ortaya çıkabilir hataların çözümü, [aşağıdaki IDebugErrorBreakpointResolution2 yöntemlerini de gerektirir.](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Kesme noktası türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktası çözümleme bilgilerini alır.|

 Kaynak kodu bir kesme noktası içinde görüntülemek için [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve/veya [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)yöntemlerini uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
