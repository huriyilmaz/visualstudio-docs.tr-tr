---
title: Bağlama kesme noktaları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903232"
---
# <a name="bind-breakpoints"></a>Bağlama kesme noktaları
Kullanıcı bir kesme noktası ayarlarsa, belki de **F9**tuşuna basarak, IDE isteği tanımlar ve hata ayıklama oturumunun kesme noktasını oluşturmasını ister.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama
 Kesme noktası tarafından etkilenen kod veya veriler henüz kullanılamadığından bir kesme noktası ayarlamak iki adımlı bir işlemdir. İlk olarak, kesme noktası açıklanmalıdır ve kod veya veri kullanılabilir hale geldiğinde, bu kod veya verilere aşağıdaki gibi bağlanmalıdır:

1. Kesme noktası ilgili hata ayıklama altyapılarından (DEs) istenir ve ardından kesme noktası, kullanılabilir hale geldiğinde koda veya verilere bağlanır.

2. Kesme noktası isteği, ilgili tüm DEs 'e gönderen hata ayıklama oturumuna gönderilir. Kesme noktasını işlemeye seçen her türlü DE karşılık gelen bir bekleyen kesme noktası oluşturur.

3. Hata ayıklama oturumu bekleyen kesme noktalarını toplar ve bunları hata ayıklama paketine (Visual Studio 'nun hata ayıklama bileşeni) geri gönderir.

4. Hata ayıklama paketi, bekleyen kesme noktasını koda veya verilere bağlamak için hata ayıklama oturumuna sorar. Hata ayıklama oturumu bu isteği ilgili tüm DEs 'e gönderir.

5. Ayrıca, kesme noktasını bağlayabiliyorsa, hata ayıklama oturumuna bir kesme noktası bağlı olay gönderir. Aksi takdirde, bunun yerine bir kesme noktası hata olayı gönderir.

## <a name="pending-breakpoints"></a>Bekleyen kesme noktaları
 Bekleyen bir kesme noktası birden çok kod konumuna bağlanabilir. Örneğin, bir C++ şablonu için bir kaynak kodu satırı, şablondan oluşturulan her kod dizisine bağlanabilir. Hata ayıklama oturumu, olay gönderilirken bir kesme noktasına dayalı kod bağlamlarını numaralandırmak için kesme noktası ile bağlantılı bir olay kullanabilir. Daha sonra daha fazla kod bağlamı bağlanabilir, bu nedenle her bir bağlama isteği için birden çok kesme noktası bağlı olay gönderebilir. Ancak, bir DE bağlama isteği başına yalnızca bir kesme noktası hata olayı göndermelidir.

## <a name="implementation"></a>Uygulama
 Programlı olarak, hata ayıklama paketi oturum hata ayıklama Yöneticisi 'ni (SDM) çağırır ve bir [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) yapısını sarmalayan bir [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabirimi sağlar ve bu da ayarlanacak kesme noktasını tanımlar. Kesme noktaları pek çok form olabilir, ancak sonuçta bir kod veya veri bağlamına çözümlenirler.

 SDM, [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yöntemini çağırarak her ilgisi olan bu çağrıyı geçirir. Ayrıca, kesme noktasını tanıtıcıyı seçerse, bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi oluşturur ve döndürür. SDM bu arabirimleri toplar ve bunları hata ayıklama paketine tek bir arabirim olarak geri geçirir `IDebugPendingBreakpoint2` .

 Şimdiye kadar, hiçbir olay üretilmez.

 Hata ayıklama paketi daha sonra, ve ile uygulanan [bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)çağırarak, bekleyen kesme noktasını koda veya verilere bağlamayı dener.

 Kesme noktası bağlıysa, DE hata ayıklama paketine bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) olay arabirimi gönderir. Hata ayıklama paketi, bir veya daha fazla [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimi döndüren [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)çağırarak kesme noktasıyla bağlantılı tüm kod bağlamlarını (veya tek veri bağlamını) numaralandırmak için bu arabirimi kullanır. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) arabirimi bir [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) arabirimi döndürür ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) kodu veya veri bağlamını içeren [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) bir UNION döndürür.

 DE, kesme noktasını bağlayamıyor, hata ayıklama paketine tek bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) Event arabirimi gönderir. Hata ayıklama paketi, [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)ve ardından [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)' ı çağırarak hata türünü (hata veya uyarı) ve bilgilendirici iletiyi alır. Bu, hata türünü ve iletisini içeren bir [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısı döndürür.

 Bir kesme noktası işler, ancak bağlanamaz, türünde bir hata döndürür `BPET_TYPE_ERROR` . Hata ayıklama paketi bir hata iletişim kutusu görüntüleyerek yanıt verir ve IDE, kaynak kodu satırının soluna kesme işareti glifin içine bir ünlem karakteri koyar.

 Bir kesme noktasını da işlediğinde, bağlanamaz, ancak başka bir durum da bağlayabilir, bir uyarı döndürür. IDE, kaynak kodu satırının soluna bir soru karakteri yazarak yanıt verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
