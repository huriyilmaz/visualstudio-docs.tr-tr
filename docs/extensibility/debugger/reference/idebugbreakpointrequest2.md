---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d31b7cfe2480fa3b16a4d3c8c08185194fec6b79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951205"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Bu arabirim, herhangi bir kesme noktası türü oluşturmak ve bağlamak için gereken bilgileri temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Oturum hata ayıklama Yöneticisi (SDM), bu arabirimi genellikle uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı (DE), bekleyen bir kesme noktası oluşturmak için bu arabirimi [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) çağrısı aracılığıyla alır. [Getbreakpointrequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) çağrısı, bu arabirimi de öğesinden alabilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBreakpointRequest2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Bu kesme noktası isteğinin kesme noktası konum türünü alır.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Bu kesme noktası isteğini açıklayan kesme noktası istek bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Hata Ayıklanan program yüklendikten sonra [bağlama](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) çağrısı, bekleyen bir kesme noktasını programda istenen konuma bağlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
