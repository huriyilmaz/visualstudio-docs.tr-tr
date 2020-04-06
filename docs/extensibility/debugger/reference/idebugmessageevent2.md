---
title: IDebugMessageEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727365"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından Visual Studio'ya kullanıcıdan yanıt gerektiren bir ileti göndermek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, Visual Studio'ya kullanıcı yanıtı gerektiren bir ileti göndermek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

 Bu arabirimin uygulanması, Visual Studio'nun [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) çağrısını DE'ye iletmelidir. Örneğin, bu DE'nin ileti işleme iş parçacığına gönderilen bir ileti yle yapılabilir veya bu arabirimi uygulayan nesne DE'ye bir `IDebugMessageEvent2::SetResponse`başvuru tutabilir ve verilen yanıtla DE'ye geri çağrıyapabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve yanıt gerektiren bir kullanıcıya bir ileti görüntülemek için bu olay nesnesi gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugMessageEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|İletinin görüntülenmesini alır.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|İleti kutusundan yanıtı ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Belirli bir ileti için kullanıcıdan belirli bir yanıt gerektiriyorsa DE bu arabirimi kullanır. Örneğin, bir programa uzaktan iletme girişiminden sonra DE bir "Erişim Reddedildi" iletisi alırsa, DE `IDebugMessageEvent2` bu özel iletiyi ileti kutusu stiline `MB_RETRYCANCEL`sahip bir olay halinde Visual Studio'ya gönderir. Bu, kullanıcının ekleme işlemini yeniden denemesini veya iptal etmesini sağlar.

 DE, win32 işlevinin `MessageBox` kurallarını izleyerek bu iletinin nasıl işleneceğini belirtir (ayrıntılar için [AfxMessageBox'a](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) bakın).

 Kullanıcıdan yanıt gerektirmeyen iletileri Visual Studio'ya göndermek için [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) arabirimini kullanın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
