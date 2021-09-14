---
description: IDebugBreakPointRequest2 arabirimi, herhangi bir kesme noktası türünü oluşturmak ve bağlamak için gereken bilgileri temsil eder.
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: df0b17c6a1696315e328121eaa305a65defe40ea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636441"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Bu arabirim, herhangi bir kesme noktası türünü oluşturmak ve bağlamak için gereken bilgileri temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Oturum hata ayıklama yöneticisi (SDM) genellikle bu arabirimi uygulamaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı (DE), bekleyen bir kesme noktası oluşturmak için [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) çağrısı aracılığıyla bu arabirimi alır. [GetBreakpointRequest çağrısı](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) bu arabirimi DE'den alabilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugBreakpointRequest2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Bu kesme noktası isteğinin kesme noktası konum türünü alır.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Bu kesme noktası isteğini açıklayan kesme noktası isteği bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklaması yapılan program yüklendikten sonra [](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) Bind çağrısı, bekleyen bir kesme noktası ile programda istenen konuma bağlanıyor.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bağlamak](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
