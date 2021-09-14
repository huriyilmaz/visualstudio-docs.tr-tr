---
description: Bu arabirim, bir kesme noktası hatasının çözünürlüğünü temsil eder.
title: IDebugErrorBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3aaed396e2038740936fd74643690b86dc80530a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634862"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
Bu arabirim, bir kesme noktası hatasının çözünürlüğünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı bu arabirimi kesme noktası desteğinin bir parçası olarak uygulamaya almaktadır. Bu arabirim, bir kesme noktası bağlamanın başarısız olduğunu rapor etmek için kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetBreakpointResolution çağrısı,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) kesme noktası bağlamanın başarısız olduğu yer hakkında bilgi sağlamak için bu arabirimi döndürür. [GetErrorBreakpoint yöntemi](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) [IDebugErrorBreakpoint2 arabirimini](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) elde ediyor.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugErrorBreakpointResolution2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Kesme noktası türünü alır.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Kesme noktası çözümleme bilgilerini alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
