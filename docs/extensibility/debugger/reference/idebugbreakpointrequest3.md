---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6e42111ca0c8b357a7f8841511cf935694a30b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893067"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Bu arabirim, herhangi bir kesme noktası türü oluşturmak ve bağlamak için gereken bilgileri temsil eder. Bu bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)uzantısıdır.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Oturum hata ayıklama Yöneticisi (SDM), bu arabirimi genellikle uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı (DE), [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)çağrısında alınan IDebugBreakpointRequest2 arabirimine [QueryInterface](/cpp/atl/queryinterface) çağırarak bu arabirime erişir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)öğesinden devralınan yöntemlere ek olarak, `IDebugBreakpointRequest3` arabirimi aşağıdaki yöntemi kullanıma sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Bu kesme noktası isteğini açıklayan kesme noktası istek bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısıyla aynı bilgilere ek bilgi sağlamak için kullanılır. Bu ek bilgiler, satıcı KIMLIĞINI (bir GUID biçiminde), izleneme noktasının adını ve bir kesme noktası kısıtlamasının adını içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
