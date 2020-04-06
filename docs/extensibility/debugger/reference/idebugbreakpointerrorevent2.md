---
title: IDebugBreakpointErrorEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735048"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) bekleyen bir kesme noktasının bir uyarı veya hata nedeniyle yüklenen bir programa bağlanamayacağını bildirir.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, kesme noktalarına verdiği desteğin bir parçası olarak bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bekleyen bir kesme noktası debugged olan programa bağlı olamaz ZAMAN DE oluşturur ve bu olay nesnesi gönderir. Olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak, programa eklendiğinde debugged olarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugBreakpointErrorEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Uyarı veya hatayı açıklayan [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimini alır.|

## <a name="remarks"></a>Açıklamalar
 Bir kesme noktası bağlandığında, bir olay SDM'ye gönderilir. Kesme noktası bağlanamıyorsa, `IDebugBreakpointErrorEvent2` bir gönderilir; aksi takdirde, bir [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gönderilir.

 Örneğin, bekleyen kesme noktasıyla ilişkili koşul ayrıştırılamadığında veya değerlendiremediğinde, bekleyen kesme noktasının şu anda bağlanamayacağına dair bir uyarı gönderilir. Kesme noktasının kodu henüz yüklenmediyse bu oluşabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
