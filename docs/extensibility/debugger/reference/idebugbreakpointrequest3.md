---
description: IDebugBreakpointRequest3 arabirimi, herhangi bir kesme noktası türünü oluşturmak ve bağlamak için gereken bilgileri temsil eder.
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 60f3900ccb8b1c502fce9c0af4288fc50ed9a63b2409207fd3a5878e0b6ff9e4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292890"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Bu arabirim, herhangi bir kesme noktası türünü oluşturmak ve bağlamak için gereken bilgileri temsil eder. [IDebugBreakpointRequest2 uzantısıdır.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Oturum hata ayıklama yöneticisi (SDM) genellikle bu arabirimi uygulamaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı (DE), [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)çağrısında alınan IDebugBreakpointRequest2 arabiriminde [QueryInterface](/cpp/atl/queryinterface) çağrısıyla bu arabirime erişir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Arabirimi, IDebugBreakpointRequest2'den](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)devralınan yöntemlere ek `IDebugBreakpointRequest3` olarak aşağıdaki yöntemi gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Bu kesme noktası isteğini açıklayan kesme noktası isteği bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, uygulama yapısı aracılığıyla DE'ye ek [bilgi BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) kullanılır. Bu ek bilgiler DE'nin satıcı kimliğini (GUID şeklinde), izleme noktası adını ve kesme noktası kısıtlaması adını içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
