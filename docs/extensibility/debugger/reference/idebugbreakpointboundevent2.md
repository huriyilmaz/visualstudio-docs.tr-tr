---
title: IDebugBreakpointBoundEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735303"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) bekleyen bir kesme noktasının yüklenen bir programa başarıyla bağlandığını bildirir.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, kesme noktalarına verdiği desteğin bir parçası olarak bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bekleyen bir kesme noktası debugged olan programa başarıyla bağlandığında DE oluşturur ve bu olay nesnesi gönderir. Olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak, programa eklendiğinde debugged olarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugBreakpointBoundEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Bağlanmakta olan bekleyen kesme noktasını alır.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Bu olaya bağlı olan kesme noktalarının bir sayıyı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Bir kesme noktası bağlandığında, bir olay SDM'ye gönderilir. Kesme noktası bağlanamıyorsa, bir [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gönderilir; aksi takdirde, bir gönderilir. `IDebugBreakpointBoundEvent2`

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
