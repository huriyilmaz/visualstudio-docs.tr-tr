---
description: Bu arabirim FRAMEıNFO yapılarını numaralandırır.
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c347b7cebd9b1417cd0a8e772cd8a247e975ea97
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226390"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Bu arabirim [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapılarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), geçerli çağrı yığınını açıklayan yapıların listesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio, hata ayıklamakta olan bir programda bir kesme noktası, özel durum veya durduruluyor olduğunda bu arabirimi almak için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 'yu çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugFrameInfo2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısını alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Bir Numaralandırıcı içindeki [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, hata ayıklamakta olan programda bir kesme noktası, özel durum veya Kullanıcı tarafından oluşturulan duraklamayı işlemeye yönelik ilk adım olarak bu arabirimi edinir. [FrameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapılarının listesi geçerli çağrı yığınını, listenin başındaki geçerli işlev çağrısını ve listenin sonundaki en eski işlev çağrısını gösterir. Her biri `FRAMEINFO` bir yığın çerçevesini, ifadelerin değerlendirilebilecek ve yerel değişkenlerin bakıdığı bağlamı temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
