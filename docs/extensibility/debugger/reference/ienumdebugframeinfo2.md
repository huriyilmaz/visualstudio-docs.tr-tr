---
title: IEnumDebugFrameInfo2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716615"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Bu arabirim, [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarını sayısallandırır.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) geçerli çağrı yığınını açıklayan yapıların bir listesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio, bir kesme noktası, özel durum veya durdurma debugged bir program oluşur bu arabirimi elde etmek için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugFrameInfo2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısını alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Bir numaralandırma dizisinde belirli sayıda [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Bir numaralandırmadaki [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, hata ayıklanan programda bir kesme noktası, özel durum veya kullanıcı tarafından oluşturulan duraklamaişlemenin ilk adımı olarak bu arabirimi elde eder. [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapıları listesi, listenin başındaki geçerli işlev çağrısı ve listenin sonundaki en eski işlev çağrısıyla geçerli çağrı yığınını temsil eder. Her `FRAMEINFO` biri bir yığın çerçevesini, ifadelerin değerlendirilebileceği ve yerel değişkenlerin bakıldığı bir bağlamı temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
