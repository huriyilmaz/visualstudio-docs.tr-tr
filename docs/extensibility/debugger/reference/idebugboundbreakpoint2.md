---
description: Bu arabirim, bir kod konumuna bağlanan bir kesme noktasını temsil eder.
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2726a2422c49335d9c95e7d500381ad1fdc0108
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167483"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Bu arabirim, bir kod konumuna bağlanan bir kesme noktasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) çağrısı bu arabirimi oluşturur. [Getbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) ve [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) çağrıları da bu arabirimi alabilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBoundBreakpoint2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Belirtilen bağlantılı kesme noktasının oluşturulduğu bekleyen kesme noktasını alır.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bu bağlantılı kesme noktasının durumunu alır.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Bu bağlantılı kesme noktası için geçerli isabet sayısını alır.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Bu kesme noktasını açıklayan kesme noktası çözünürlüğünü alır.|
|[Etkinleştirme](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Kesme noktasını etkinleştirilir veya devre dışı bırakır.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Bu bağlantılı kesme noktası için isabet sayısını ayarlar.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Bu ilişkili kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Bu ilişkili kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.|
|[Silme](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Kesme noktasını siler.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
