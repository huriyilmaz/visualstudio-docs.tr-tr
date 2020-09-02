---
title: Kesme noktası ile Ilgili Yöntemler | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739200"
---
# <a name="breakpoint-related-methods"></a>Kesme noktası ile ilgili Yöntemler
Bir hata ayıklama altyapısı (DE) kesme noktası ayarını desteklemelidir. Visual Studio hata ayıklaması aşağıdaki kesme noktası türlerini destekler:

- Bound

     Kullanıcı arabirimi aracılığıyla istendi ve belirtilen kod konumuna başarıyla bağlıydı

- Beklemede

     Kullanıcı arabirimi aracılığıyla istendi, ancak henüz gerçek yönergelere bağlanmadı

## <a name="discussion"></a>Tartışma
 Örneğin, yönergeler henüz yüklenmediği sırada bekleyen bir kesme noktası oluşur. Kod yüklendiğinde, bekleyen kesme noktaları kodu önceden belirlenmiş konumda bağlamaya çalışır, diğer bir deyişle, koda kesme yönergeleri ekler. Olaylar, başarılı bağlamayı göstermek veya bağlama hataları olduğunu bildirmek için oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

 Bekleyen bir kesme noktası Ayrıca kendi iç karşılık gelen ilişkili kesme noktaları listesini yönetir. Bir bekleyen kesme noktası, koddaki birçok kesme noktasının eklenmesine neden olabilir. Visual Studio hata ayıklama Kullanıcı arabirimi, bekleyen kesme noktalarının ve bunlara karşılık gelen ilişkili kesme noktalarının ağaç görünümünü gösterir.

 Bekleyen kesme noktalarının oluşturulması ve kullanılması, [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yönteminin yanı sıra aşağıdaki [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi yöntemlerini gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Belirtilen bir bekleyen kesme noktasının bir kod konumuna bağlanıp bağlanamayacağını belirler.|
|[Bağladığınızda](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Belirtilen bir bekleyen kesme noktasını bir veya daha fazla kod konumuna bağlar.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bekleyen bir kesme noktasının durumunu alır.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bekleyen kesme noktası oluşturmak için kullanılan kesme noktası isteğini alır.|
|[Etkinleştirme](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bekleyen bir kesme noktasının etkin durumunu değiştirir.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bekleyen bir kesme noktasından bağlantılı tüm kesme noktalarını numaralandırır.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bekleyen bir kesme noktasından kaynaklanan tüm hata kesme noktalarını numaralandırır.|
|[Silme](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bekleyen bir kesme noktasını ve bundan sonra gelen tüm kesme noktalarını siler.|

 Bağlantılı kesme noktalarını ve hata kesme noktalarını numaralandırmak için, tüm [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) ve [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)yöntemlerini uygulamanız gerekir.

 Bir kod konumuna bağlanan bekleyen kesme noktaları, aşağıdaki [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Kesme noktası içeren bekleyen kesme noktasını alır.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bir bağlantılı kesme noktasının durumunu alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Bir kesme noktasını açıklayan kesme noktası çözünürlüğünü alır.|
|[Etkinleştirme](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Kesme noktasını etkinleştirilir veya devre dışı bırakır.|
|[Silme](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Bir bağlantılı kesme noktasını siler.|

 Çözüm ve istek bilgileri aşağıdaki [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Bir çözüm tarafından temsil edilen kesme noktasının türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktasını açıklayan kesme noktası çözümleme bilgilerini alır.|

 Bağlama sırasında ortaya çıkabilecek hataların çözümlenmesi, aşağıdaki [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) yöntemlerinin uygulanmasını gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Hata kesme noktası içeren bekleyen kesme noktasını alır.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Bir hata kesme noktası tanımlayan kesme noktası hata çözümünü alır.|

 Bağlama sırasında oluşabilecek hataların çözümlenmesi, aşağıdaki [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)yöntemlerini de gerektirir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Bir kesme noktasının türünü alır.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktasının çözüm bilgilerini alır.|

 Kaynak kodu bir kesme noktasında görüntülemek için, [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve/veya [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)yöntemlerini uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
