---
title: IDebugBreakpointUnboundEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e1d15936316d08a712e3d6f3fdc7a3a73be613d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734631"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) yüklü bir programdan bağlı bir kesme noktasının bağlanmadığını bildirir.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakpointUnboundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kesme noktaları için verdiği desteğin bir parçası olarak bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 De, bağlı bir kesme noktası bağlanmamışsa bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak, programa eklendiğinde debugged olarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugBreakpointUnboundEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Bağlanmaz hale gelen kırılma noktasını alır.|
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Kopuş noktasının bağlanmamasının nedenini alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama motoru DLL veya sınıf boşaltıldığında, bu modüldeki koda bağlı tüm kesme noktaları, ayıklanan programdan çıkarılmalıdır. Bağlı `IDebugBreakpointUnboundEvent2` olmayan her kesme noktası için bir gönderilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
