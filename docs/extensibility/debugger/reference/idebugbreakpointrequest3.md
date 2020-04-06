---
title: IDebugBreakpointRequest3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734825"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Bu arabirim, herhangi bir kesme noktası oluşturmak ve bağlamak için gereken bilgileri temsil eder. [Bu IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)bir uzantısıdır.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Oturum hata ayıklama yöneticisi (SDM) genellikle bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı (DE) [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)için bir çağrı alınan IDebugBreakpointRequest2 arabiriminde [QueryInterface](/cpp/atl/queryinterface) arayarak bu arayüze erişir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugBreakpointRequest2'den](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)devralınan yöntemlere ek `IDebugBreakpointRequest3` olarak, arabirim aşağıdaki yöntemi ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Bu kesme noktası isteğini açıklayan kesme noktası isteği bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısı aracılığıyla DE'ye ek bilgi sağlamak için kullanılır. Bu ek bilgiler DE'nin satıcı kimliğini (GUID biçiminde), bir izleme noktasının adını ve kesme noktası kısıtlamasının adını içerir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
