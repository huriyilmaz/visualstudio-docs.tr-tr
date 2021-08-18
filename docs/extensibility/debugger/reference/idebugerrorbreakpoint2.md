---
description: Bu arabirim geçersiz konum, geçersiz ifade veya bekleyen kesme noktası bağlı değil (kod henüz yüklenmedi vb.) nedenlerini temsil eden bir hata veya uyarı kesme noktası temsil eder.
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b7b4b4760b6d7388a9b1179b27322b8aa4a0b13b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035091"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Bu arabirim geçersiz konum, geçersiz ifade veya bekleyen kesme noktası bağlı değil (kod henüz yüklenmedi vb.) nedenlerini temsil eden bir hata veya uyarı kesme noktası temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı bu arabirimi kesme noktası desteğinin bir parçası olarak uygulamaya almaktadır. Bu arabirim, bir kesme noktası bağlamayla ilgili sorunları rapor etmek için kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetErrorBreakpoint çağrısı bu](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) arabirimi elde ediyor. Bu arabirim [canBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) veya [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)çağrısıyla da döndürülebilirsiniz [(IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) arabirimiyle temsil edilen bir listenin parçası olarak).

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugErrorBreakpoint2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Hataya neden olan bekleyen kesme noktası alır.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Hatayı açıklayan kesme noktası hata çözümlemesi alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
