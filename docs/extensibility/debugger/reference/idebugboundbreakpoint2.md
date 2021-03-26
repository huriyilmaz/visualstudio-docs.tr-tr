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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8a48ffcb3c0409839ec9323679e396a7e23b8f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088828"
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
