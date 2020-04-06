---
title: IEnumDebugErrorBreakpoints2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716891"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Bu arabirim, bekleyen bir kesme noktasıyla ilişkili hata kesme noktalarını doğrular.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kesme noktaları için verdiği desteğin bir parçası olarak bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio, bağlanamayan kesme noktalarının listesini temsil eden bu arabirimi veya bağlı olmayan kesme noktaları nın listesini temsil eden bu arabirimi elde etmek için [EnumErrorBreakpoints'i](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) almak için [CanBind'i](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugErrorBreakpoints2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Numaralandırma sırasında belirtilen sayıda hata kesme noktası alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Numaralandırma sırasında belirli sayıda hata kesme noktasını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Bir numaralandırmadaki hata kesme noktalarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, her biri bağlanamayan ve neden bağlanamayan bir kesme noktası nı açıklayan [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimlerinin bir listesini tutar. Visual Studio, `IEnumDebugErrorBreakpoint2` IDE'de gösterilen kesme noktalarını güncelleştirmek için arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
