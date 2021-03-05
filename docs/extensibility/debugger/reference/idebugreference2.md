---
description: Bu arabirim bir yığın çerçevesi özelliğine veya başka bir özelliğe başvuruyu temsil eder.
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 04d9795388b2a079d0eb7ac1d787bf92de6cdff4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165858"
---
# <a name="idebugreference2"></a>IDebugReference2
Bu arabirim bir yığın çerçevesi özelliğine veya başka bir özelliğe başvuruyu temsil eder.

> [!NOTE]
> `IDebugReference2` gelecekte kullanılmak üzere ayrılmıştır ve tüm yöntemleri döndürmelidir `E_NOTIMPL` .

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, belirli bir değer türüne başvuruyu temsil etmek için DE uygular. Örneğin, değer bir ifade değerlendirmesinin sonucu olarak sayısal bir değer, bellek görüntülemek için kullanılan bir bellek bağlamı veya bir kayıt listesi ve bunların değerleri olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi edinmek için [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) öğesini çağırın. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) ve [Getderivedmostreference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) Ayrıca bu arabirimi de döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugReference2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Bu başvuruyu açıklayan [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısını alır.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Bu başvurunun değerini bir dizeden ayarlar.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Bu başvurunun değerini başka bir başvuruya ayarlar.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Bu başvurunun alt öğelerini numaralandırır.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Bu başvurunun üst öğesini alır.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Bu başvurunun en fazla türetilmiş başvurusunu alır.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Bu başvurunun başvurduğu bellek baytlarını alır.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Bu başvuru için bir bellek bağlamı alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Bu başvurunun bayt cinsinden boyutunu alır.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Bu başvuru türünü ayarlar.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Bu başvuruyu başka bir ile karşılaştırır.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu "Property" kullanımı, bu `IDebugReference2` tür bir varlığı temsil edebilir ancak bir sınıfın üye değişkeni anlamı olan ile karıştırılmamalıdır.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) bir özelliği temsil ederken, `IDebugReference2` genellikle hata ayıklanan programdaki bir nesneye yapılan bir özelliğe başvuruyu temsil eder.

 Bir özellik ve başvuru arasındaki temel fark, bir özelliğin bir nesnenin adlandırılmış örneğine başvurduğu, ancak bir başvurunun adlandırılmamış bir örneğe başvurduğu anlamına gelir. Örneğin, bir özellik programın yığın içindeki bir nesneye başvurabilir `"a.b"` . Başka bir özellik, ile aynı nesneye başvurabilir `"c.d"` . Bu özelliğe başvurma yöntemi, bunun `"a.b"` ya da `"c.d"` kapsam içinde olmasını gerektirir. Aynı nesneye bir başvuru Nameless; nesne, bu nesnenin belleği geçerli olduğu sürece başvuruda bulunabilir.

 Bir `IDebugProperty2` arabirim bir ada, türe ve adrese sahip bir değer olarak düşünülebilir. `IDebugReference2`Diğer taraftan, bir tür ve bir adres olarak düşünülebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
