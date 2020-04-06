---
title: IDebugPendingBreakpoint2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725642"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Bu arabirim, kod konumuna bağlanmaya hazır bir kesme noktasını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kesme noktaları için verdiği desteğin bir parçası olarak bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) için yapılan bir arama, [iDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabiriminden bekleyen bir kesme noktası oluşturur. [Bind'e](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yapılan arama, programdaki bağlı bir kesme noktasını temsil eden bir `IDebugBreakpoint2` arabirim oluşturur.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPendingBreakpoint2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bekleyen bu kesme noktasının kod konumuna bağlanıp bağlanamayacağını belirler.|
|[Bağla](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bekleyen bu kesme noktasını bir veya daha fazla kod konumuna bağlar.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bekleyen bu kesme noktasının durumunu alır.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bu bekleyen kesme noktasını oluşturmak için kullanılan kesme noktası isteğini alır.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Bekleyen bu kesme noktasının sanallaştırılmış durumunu geçiştir.|
|[Etkinleştir](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bekleyen bu kesme noktasının etkin durumunu geçişe yönlendirin.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Bekleyen bu kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Bekleyen kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bekleyen kesme noktasından bağlı tüm kesme noktalarını osayılar.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bu bekleyen kesme noktasından kaynaklanan tüm hata kesme noktalarını oyalar.|
|[Sil](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bekleyen bu kesme noktasını ve ondan bağlanan tüm kesme noktalarını siler.|

## <a name="remarks"></a>Açıklamalar
 `IDebugPendingBreakpoint2`bir veya birden çok programa uygulanabilecek bir kesme noktasını koda bağlamak için gereken tüm gerekli bilgilerin sağlayıcısı olarak düşünülebilir.

 Bekleyen bir kesme noktası, birden fazla bağlama kesme noktası üretebilir. Örneğin, C++stili şablonundaki bir kesme noktası, bu şablonun her benzersiz örneği için bağlı bir kesme noktası oluşturabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
