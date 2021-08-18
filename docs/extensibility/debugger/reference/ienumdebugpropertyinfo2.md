---
description: Bu arabirim, DEBUG_PROPERTY_INFO numaralar.
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 83e3f094763b19b712273563ce1446f07b1c1efd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152750"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Bu arabirim, DEBUG_PROPERTY_INFO [numaralar.](../../../extensibility/debugger/reference/debug-property-info.md)

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), belirli bir özelliğin bilgilerini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Belirli bir özelliğin küçüklerini temsil eden bu arabirimi elde etmek için [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağrısı. Belirli bir yığın çerçevesinin özelliklerini temsil eden bu arabirimi elde etmek için [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugPropertyInfo2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Bir numaralama [dizisinde DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) sayıda veri yapısı alınır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Bir numaralama [dizisinde DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) sayıda yapıyı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Numaralayıcıda [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Genel olarak, bir özellik bir ad, değer, adres ve türün yanı sıra ilişkili özellik nesnesine veya yığın çerçevesine uygun diğer tüm bilgileri içeren bir bilgi hiyerarşisidir. Daha [fazla bilgi için bkz. IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
