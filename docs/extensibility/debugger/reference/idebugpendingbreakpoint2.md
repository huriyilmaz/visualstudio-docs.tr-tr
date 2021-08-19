---
description: Bu arabirim, bir kod konumuna bağlanmaya yönelik bir kesme noktasını temsil eder.
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 96de5582c4ae60c9775af5ca72e5a15b8a370a7e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160081"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Bu arabirim, bir kod konumuna bağlanmaya yönelik bir kesme noktasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) çağrısı, bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabiriminden bekleyen bir kesme noktası oluşturur. [Bağlama](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) çağrısı `IDebugBreakpoint2` , programda bağlı bir kesme noktasını temsil eden bir arabirim oluşturur.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPendingBreakpoint2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bu bekleyen kesme noktasının bir kod konumuna bağlanıp bağlanamayacağını belirler.|
|[Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bu bekleyen kesme noktasını bir veya daha fazla kod konumuna bağlar.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bu bekleyen kesme noktasının durumunu alır.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bu bekleyen kesme noktasını oluşturmak için kullanılan kesme noktası isteğini alır.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Bu bekleyen kesme noktasının sanallaştırılmış durumuna geçiş yapar.|
|[Etkinleştirme](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bu bekleyen kesme noktasının etkin durumuna geçer.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Bu bekleyen kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Bu bekleyen kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bu bekleyen kesme noktasından bağlantılı olan tüm kesme noktalarını numaralandırır.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bu bekleyen kesme noktasından kaynaklanan tüm hata kesme noktalarını numaralandırır.|
|[Silme](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bu bekleyen kesme noktasını ve onunla bağlantılı tüm kesme noktalarını siler.|

## <a name="remarks"></a>Açıklamalar
 `IDebugPendingBreakpoint2` , bir veya daha fazla program için uygulanabilen bir kesme noktasını bağlamak için gereken tüm gerekli bilgilerin bir sağlayıcısı olarak düşünülebilir.

 Bekleyen bir kesme noktası, büyük olasılıkla birden fazla bağlantılı kesme noktası üretebilir. Örneğin, C++ stili şablondaki bir kesme noktası, söz konusu şablonun her benzersiz örneği için bir bağlantılı kesme noktası üretebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
