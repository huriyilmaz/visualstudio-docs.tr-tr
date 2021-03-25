---
description: Bu arabirim, bir uyarı veya hata nedeniyle, bekleyen bir kesme noktasının yüklenmiş bir programa bağlanamadığı bir oturum hata ayıklama Yöneticisi 'ne (SDM) söyler.
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7ebfa6b5d1cc2a0fe1a03c9e70952c5cec1a74e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054541"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Bu arabirim, bir uyarı veya hata nedeniyle, bekleyen bir kesme noktasının yüklenmiş bir programa bağlanamadığı bir oturum hata ayıklama Yöneticisi 'ne (SDM) söyler.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 DE bu arabirimi, kesme noktaları desteğinin bir parçası olarak uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` ).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bekleyen bir kesme noktası hata ayıklamakta olan programa bağlanalınmazsa bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBreakpointErrorEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Uyarı veya hatayı açıklayan [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimini alır.|

## <a name="remarks"></a>Açıklamalar
 Kesme noktası her bağlandığında, SDM 'ye bir olay gönderilir. Kesme noktası bağlanamaz, bir `IDebugBreakpointErrorEvent2` gönderilir; Aksi takdirde, bir [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gönderilir.

 Örneğin, bekleyen kesme noktasıyla ilişkili Koşul ayrıştırılamıyor veya değerlendiremediğinde, bekleyen kesme noktasının şu anda bağlanmayacağı bir uyarı gönderilir. Kesme noktası kodu henüz yüklenmediyse bu durum oluşabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
