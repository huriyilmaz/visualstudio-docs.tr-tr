---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d52aad69397be315cf9c06b5f49a2c55d2fce28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929530"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Bu arabirim, bekleyen kesme noktası veya kesme noktası bağlantılı olayla ilişkili olan ilişkili kesme noktalarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular. Kesme noktaları destekleniyorsa bu arabirimin uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio çağrıları:

- Tetiklenen tüm kesme noktalarının listesini temsil eden bu arabirimi elde etmek için [reakal alındı](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) .

- Bu arabirimi, bağlanan tüm kesme noktalarının bir listesini temsil eden [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

- Bu arabirimi, bekleyen kesme noktasına bağlanan tüm kesme noktalarının listesini temsil eden [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugBoundBreakpoints2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantılı kesme noktası alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantılı kesme noktası atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Bir Numaralandırıcı içindeki bağlantılı kesme noktalarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, IDE 'deki kesme noktalarının görüntülenmesini güncelleştirmek için bu arabirim tarafından temsil edilen bağlantılı kesme noktalarını kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
