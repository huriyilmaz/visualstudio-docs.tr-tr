---
description: Bu arabirim, bekleyen bir kesme noktası veya kesme noktası bağlı olayı ile ilişkili sınır kesme noktaları numaralar.
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: efac05deb9d528b66f93d69cdd071113bb5d2b51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118378"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Bu arabirim, bekleyen bir kesme noktası veya kesme noktası bağlı olayı ile ilişkili sınır kesme noktaları numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kesme noktası desteğinin bir parçası olarak bu arabirimi uygulamaya almaktadır. Kesme noktaları destekleniyorsa bu arabirimin uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio çağrıları:

- Tetiklenen tüm kesme noktaları listesini temsil eden bu arabirimi elde etmek için [EnumBreakpoints.](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)

- Bu arabirime bağlanılmış olan tüm kesme noktaları listesini temsil eden [enumBoundBreakpoints.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

- Bekleyen kesme noktasıyla ilişkili tüm kesme noktaları listesini temsil eden bu arabirimi elde etmek için [EnumBoundBreakpoints.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugBoundBreakpoints2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Bir numaralama dizisinde belirtilen sayıda bağlı kesme noktası alma.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Bir numaralama dizisinde belirtilen sayıda sınır kesme noktası atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Bir numaralayıcıda bağlı kesme noktası sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, IDE'de kesme noktaları güncelleştirmeyi güncelleştirmek için bu arabirim tarafından temsil edilen bağlı kesme noktaları kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
