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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072490"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Bu arabirim, bağlı bir kesme noktası açıklayan bilgileri temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kesme noktası desteğinin bir parçası olarak bu arabirimi uygulamaya almaktadır. Bu arabirim, kullanıcı bir kesme noktası özelliklerini görüntülerken oturum hata ayıklama yöneticisinin kullandığı bir bağlı kesme noktası açıklaması sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetBreakpointResolution çağrısı bu](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
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
