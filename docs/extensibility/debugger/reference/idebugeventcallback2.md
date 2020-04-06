---
title: IDebugEventCallback2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729891"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Bu arabirim hata ayıklama altyapısı (DE) tarafından hata ayıklama olayları nı oturum hata ayıklama yöneticisine (SDM) göndermek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]hata ayıklama altyapısından olayları almak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı genellikle SDM [Ekle,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md)veya [LaunchSuspended'i](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)aradığında bu arabirimi alır. Hata ayıklama altyapısı [Olay'ı](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)arayarak Olayları SDM'ye gönderir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEventCallback2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Hata ayıklama olayları bildirimini SDM'ye gönderir.|

## <a name="remarks"></a>Açıklamalar
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) bir `IDebugEventCallback2` arabirim aldıklarını belirtse de, bu durum böyle değildir ve arabirim işaretçisi her zaman null bir değer olacaktır. Bunun yerine, hata ayıklama `IDebugEventCallback2` altyapısı ekle, [ekle](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)veya [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)için çağrıda alınan arabirimi kullanmalıdır.

 Bir paket yönetilen kodda [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) uygularsa, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> [Olay'a](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)geçirilen çeşitli arabirimlerde çağrılması önerilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
