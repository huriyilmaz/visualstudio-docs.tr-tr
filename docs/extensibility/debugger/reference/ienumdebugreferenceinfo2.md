---
title: IEnumDebugReferenceInfo2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715277"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Bu arabirim [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıları sayısallandırır.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bellekteki nesnelere yapılan başvurular için verdiği desteğin bir parçası olarak bu arabirimi uygular. Bu arabirim yalnızca başvurular desteklenirse uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arayüzü elde etmek için [EnumChildren'ı](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) arar.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugReferenceInfo2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Numaralandırma sırasında belirli sayıda [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısı alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Numaralandırma dizisinde belirtilen sayıda [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıyı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Bir numaralandırmadaki [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıların sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Başvuru aslında bir tür ve adrestir, özellik ise bir ad, tür ve adrestir. Başvuru, başvurulan nesne bellekte var olduğu sürece devam eder. Daha fazla bilgi için [IDebugReference2'ye](../../../extensibility/debugger/reference/idebugreference2.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
