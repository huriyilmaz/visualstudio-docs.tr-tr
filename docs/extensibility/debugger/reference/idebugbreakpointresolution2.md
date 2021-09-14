---
description: Bu arabirim, bağlı bir kesme noktası açıklayan bilgileri temsil eder.
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1fb8883374a84a25d27370fbe43e41ebe31025d0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636401"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Bu arabirim, bağlı bir kesme noktası açıklayan bilgileri temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kesme noktası desteğinin bir parçası olarak bu arabirimi uygulamaya almaktadır. Bu arabirim, kullanıcı bir kesme noktası özelliklerini görüntülerken oturum hata ayıklama yöneticisinin kullandığı bağlı bir kesme noktası açıklaması sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetBreakpointResolution çağrısı bu](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugBreakpointResolution2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Bu çözümlemeyle temsil edilen kesme noktası türünü alır.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Bu kesme noktası açıklayan kesme noktası çözümleme bilgilerini alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
