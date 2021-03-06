---
description: Bu arabirim DEBUG_REFERENCE_INFO yapılarını numaralandırır.
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89dd664d7b54ce451c2d3a303b3da1c7ad2b13e8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224180"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Bu arabirim [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapılarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi bellekteki nesnelere yapılan başvurular için destek kapsamında uygular. Bu arabirim yalnızca başvuruların desteklenmesinin ardından uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arabirimi edinmek için [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 'ı çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugReferenceInfo2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Sabit Listesi dizisinde belirtilen sayıda [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısını alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Bir Numaralandırıcı içindeki [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir başvuru temelde bir tür ve adrestir, ancak özellik bir ad, tür ve adrestir. Bir başvuru, nesne içinde bulunduğu sürece devam ediyor. Daha fazla bilgi için bkz. [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
