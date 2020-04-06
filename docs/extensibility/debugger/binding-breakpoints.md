---
title: Bağlama Kesme Noktaları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739235"
---
# <a name="bind-breakpoints"></a>Kesme noktalarını bağlama
Kullanıcı bir kesme noktası ayarlarsa, belki **f9**tuşuna basarak, IDE isteği formüle eder ve kesme noktası oluşturmak için hata ayıklama oturumu ister.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama
 Kesme noktasından etkilenen kod veya veriler henüz kullanılamayabilir, çünkü kesme noktası ayarlama işlemi iki adımlı bir işlemdir. İlk olarak, kesme noktası açıklanmalı ve ardından kod veya veri kullanılabilir hale geldikçe, aşağıdaki gibi bu koda veya verilere bağlı olmalıdır:

1. Kesme noktası ilgili hata ayıklama motorlarından (DEs) istenir ve sonra kesme noktası kullanılabilir hale geldikçe koda veya verilere bağlanır.

2. Kesme noktası isteği hata ayıklama oturumuna gönderilir ve bu da ilgili tüm DE'lere gönderilir. Kesme noktasını işlemeyi seçen herhangi bir DE, karşılık gelen bekleyen bir kesme noktası oluşturur.

3. Hata ayıklama oturumu bekleyen kesme noktalarını toplar ve bunları hata ayıklama paketine (Visual Studio'nun hata ayıklama bileşeni) geri gönderir.

4. Hata ayıklama paketi, bekleyen kesme noktasını kodveya verilere bağlamak için hata ayıklama oturumuna izin ister. Hata ayıklama oturumu bu isteği ilgili tüm DEs'lere gönderir.

5. DE kesme noktasını bağlayabiliyorsa, kesme noktası bağlama olayı hata ayıklama oturumuna geri gönderir. Değilse, bunun yerine bir kesme noktası hata olayı gönderir.

## <a name="pending-breakpoints"></a>Bekleyen kesme noktaları
 Bekleyen bir kesme noktası birden çok kod konumuna bağlanabilir. Örneğin, C++ şablonu için kaynak kodu satırı şablondan oluşturulan her kod dizisine bağlanabilir. Hata ayıklama oturumu, olayın gönderildiği anda bir kesme noktasına bağlı kod bağlamlarını ayıklamak için kesme noktası bağlama olayı kullanabilir. Daha fazla kod bağlamı daha sonra bağlanabilir, bu nedenle DE her bağlama isteği için birden çok kesme noktası bağlama olayı gönderebilir. Ancak, bir DE bağlama isteği başına yalnızca bir kesme noktası hata olayı göndermelidir.

## <a name="implementation"></a>Uygulama
 Programlı olarak, hata ayıklama paketi oturum hata ayıklama yöneticisini (SDM) çağırır ve ayarlanacak kesme noktasını açıklayan [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) yapısını saran bir [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabirimi verir. Kesme noktaları birçok biçimde olsa da, sonuçta bir kod veya veri bağlamına çözüm.

 SDM, [createPendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yöntemini arayarak bu çağrıyı ilgili her DE'ye iletmektedir. DE kesme noktasını işlemeyi seçerse, bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi oluşturur ve döndürür. SDM bu arabirimleri toplar ve bunları tek `IDebugPendingBreakpoint2` bir arabirim olarak hata ayıklama paketine geri geçirir.

 Şimdiye kadar hiçbir olay oluşturulmadı.

 Hata ayıklama paketi daha sonra de tarafından uygulanan [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)çağırarak bekleyen kesme noktasını kod veya veriye bağlamaya çalışır.

 Kesme noktası bağlıysa, DE hata ayıklama paketine bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) olay arabirimi gönderir. Hata ayıklama paketi, bir veya daha fazla [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimi döndüren [EnumBoundBreakpoints'i](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)arayarak kesme noktasına bağlı tüm kod bağlamlarını (veya tek veri bağlamını) ayırmak için bu arabirimi kullanır. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) arabirimi bir [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) arabirimi döndürür ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) kod veya veri bağlamını içeren [bir BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) birleşim döndürür.

 DE kesme noktasını bağlayamıyorsa, hata ayıklama paketine tek bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) olay arabirimi gönderir. Hata ayıklama paketi [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)çağırarak hata türü (hata veya uyarı) ve bilgilendirme iletisi alır, [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)takip . Bu, hata türü ve iletiiçeren [bir BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısı döndürür.

 Bir DE kesme noktası işleyebilir ancak bağlamak değil, türünde `BPET_TYPE_ERROR`bir hata döndürür. Hata ayıklama paketi bir hata iletişim kutusu görüntüleyerek yanıt verir ve IDE, kesme noktası glyph'inin içine kaynak kod satırının soluna bir ünlem glyph'si yerleştirir.

 Bir DE bir kesme noktası işlerse, bağlayamıyorsa, ancak başka bir DE bağlanabilirse, bir uyarı döndürür. IDE, kaynak kod satırının solundaki kesme noktası glyph'inin içine bir soru glyph'si yerleştirerek yanıt verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
