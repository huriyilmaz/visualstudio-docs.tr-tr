---
title: Kesme Noktaları Bağlama | Microsoft Docs
description: IDE'nin kesme noktası isteğini nasıl formüle etmeyi öğrenin ve kullanıcı bir kesme noktası ayarlarken kesme noktası oluşturmak için hata ayıklama oturumunu nasıl istemler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 128877b9a5324f78eb4b935586020bbdb999fdf5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051072"
---
# <a name="bind-breakpoints"></a>Bağlama kesme noktaları
Kullanıcı **F9** tuşuna basarak bir kesme noktası ayarlarsa, IDE isteği formüle ediyor ve kesme noktası oluşturmak için hata ayıklama oturumuna başvurur.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama
 Kesme noktası ayarı iki adımlı bir işlemdir çünkü kesme noktası tarafından etkilenen kod veya veriler henüz kullanılamıyor olabilir. İlk olarak kesme noktası açık olmalı ve ardından kod veya veriler kullanılabilir hale geldi mi, bu koda veya verilere aşağıdaki gibi bağlı olmalıdır:

1. Kesme noktası ilgili hata ayıklama altyapılarından (DE' ler) ister ve ardından kesme noktası kullanılabilir olduğunda koda veya verilere bağlı olur.

2. Kesme noktası isteği, tüm ilgili DE'lere gönderen hata ayıklama oturumuna gönderilir. Kesme noktası işlemeyi seçen herhangi bir DE karşılık gelen bekleyen bir kesme noktası oluşturur.

3. Hata ayıklama oturumu bekleyen kesme noktaları toplar ve bunları hata ayıklama paketine geri gönderir (hata ayıklama bileşeninin Visual Studio).

4. Hata ayıklama paketi, bekleyen kesme noktası kodunu veya verilerine bağlamak için hata ayıklama oturumunu ister. Hata ayıklama oturumu bu isteği tüm ilgili DE'lere gönderir.

5. DE kesme noktası bağlayabilecekse, hata ayıklama oturumuna bir kesme noktası bağlı olayı geri gönderir. Yoksa, bunun yerine bir kesme noktası hata olayı gönderir.

## <a name="pending-breakpoints"></a>Bekleyen kesme noktaları
 Bekleyen bir kesme noktası birden çok kod konuma bağlanabilir. Örneğin, bir C++ şablonu için kaynak kod satırı, şablondan oluşturulan her kod dizisine bağlanabilir. Hata ayıklama oturumu, olay gönderildiği sırada bir kesme noktasıyla ilişkili kod bağlamlarını numaralara ayıklamak için kesme noktası bağlı olayı kullanabilir. Daha fazla kod bağlamı daha sonra bağlanabilir, bu nedenle DE her bağlama isteği için birden çok kesme noktası bağlı olay gönderebilir. Ancak, bir DE bağlama isteği başına yalnızca bir kesme noktası hata olayı göndermeli.

## <a name="implementation"></a>Uygulama
 Program aracılığıyla, hata ayıklama paketi oturum hata ayıklama yöneticisini (SDM) çağırarak bir [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) yapısını sarmalar ve ayarlanacak kesme noktası açıklayan [bir IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabirimi verir. Kesme noktaları birçok farklı biçime sahip olsa da bir kod veya veri bağlamına çözüm olur.

 SDM, [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yöntemini çağırarak bu çağrıyı ilgili her DE'ye iletir. DE kesme noktası işlemeyi seçerse, bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi oluşturur ve döndürür. SDM bu arabirimleri toplar ve bunları tek bir arabirim olarak hata ayıklama paketine `IDebugPendingBreakpoint2` geri iletir.

 Şu ana kadar hiçbir olay oluşturulmadı.

 Ardından hata ayıklama paketi, DE tarafından uygulanan [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)çağrısıyla bekleyen kesme noktasıyla koda veya verilere bağlamayı çalışır.

 Kesme noktası bağlı ise DE, hata ayıklama paketine [bir IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) olay arabirimi gönderir. Hata ayıklama paketi, bir veya daha fazla [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimi döndüren [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)çağrısıyla kesme noktasıyla ilişkili tüm kod bağlamlarını (veya tek veri bağlamını) numaralandıracak şekilde bu arabirimi kullanır. [GetBreakpointResolution arabirimi](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) [bir IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) arabirimi döndürür ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) kod veya veri bağlamını [içeren BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) bir BP_RESOLUTION_INFO birlikte döndürür.

 DE kesme noktası bağlanamazsa, hata ayıklama paketine tek bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) olay arabirimi gönderir. Hata ayıklama paketi, [GetErrorBreakpoint,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)ardından [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)çağırarak hata türünü (hata veya uyarı) ve bilgilendirme iletisini alır. Bu, [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) ve iletiyi içeren bir hata yapısı döndürür.

 DE bir kesme noktası işlese ama bağlayamazsa türünde bir hata `BPET_TYPE_ERROR` döndürür. Hata ayıklama paketi bir hata iletişim kutusu görüntüleyerek yanıt verir ve IDE, kaynak kod çizgisinin sol tarafından kesme noktası glyph içine bir ünlem işareti yer alır.

 DE bir kesme noktası işlese, bağlayamazsa, ancak başka bir DE bunu bağsıyorsa, bir uyarı döndürür. IDE, kaynak kod çizgisinin sol tarafından kesme noktası glyph içine bir soru işareti yerleştirerek yanıt verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
