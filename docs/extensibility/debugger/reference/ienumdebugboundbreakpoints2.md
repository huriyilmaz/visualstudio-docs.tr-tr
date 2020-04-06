---
title: IEnumDebugBoundBreakpoints2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717450"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Bu arabirim, bekleyen bir kesme noktası veya kesme noktası bağlama olayıyla ilişkili bağlama kesme noktalarını doğrular.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kesme noktaları için verdiği desteğin bir parçası olarak bu arabirimi uygular. Kesme noktaları desteklenirse bu arabirim uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio aramaları:

- Tetiklenen tüm kesme noktalarının listesini temsil eden bu arabirimi elde etmek için [EnumBreakpoints.](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) bağlı tüm kesme noktalarının bir listesini temsil eden bu arabirimi elde etmek için.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) bekleyen kesme noktasına bağlı tüm kesme noktalarının listesini temsil eden bu arabirimi elde etmek için.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugBoundBreakpoints2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Numaralandırma sırasında belirli sayıda bağlı kesme noktası alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Numaralandırma sırasında belirli sayıda bağlı kesme noktasını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Bir numaralandırmada bağlı kesme noktalarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, IDE'deki kesme noktalarının ekranını güncelleştirmek için bu arabirim tarafından temsil edilen bağlı kesme noktalarını kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
