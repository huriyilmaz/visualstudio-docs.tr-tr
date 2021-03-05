---
description: Bu arabirim, geçersiz konum, geçersiz ifade veya bekleyen kesme noktasının bağlı olmadığı nedenleri (kod henüz yüklenmedi, vb.) gibi bir hata veya uyarı kesme noktasını temsil eder.
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91697ebad462f3d1e953aa42d74bf5a96757886a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153163"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Bu arabirim, geçersiz konum, geçersiz ifade veya bekleyen kesme noktasının bağlı olmadığı nedenleri (kod henüz yüklenmedi, vb.) gibi bir hata veya uyarı kesme noktasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir hata ayıklama altyapısı, bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular. Bu arabirim, kesme noktası bağlama ile ilgili sorunları raporlamak için kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) çağrısı bu arabirimi edinir. Bu arabirim, [Canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) veya [enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)çağrısıyla da döndürülebilir (bir [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) arabirimi tarafından temsil edilen bir listenin parçası olarak).

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugErrorBreakpoint2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Hataya neden olan bekleyen kesme noktasını alır.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Hatayı açıklayan kesme noktası hata çözümünü alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
