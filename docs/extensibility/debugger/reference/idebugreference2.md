---
description: Bu arabirim, bir yığın çerçevesi özelliğine veya başka bir özelle ilgili bir başvuru temsil eder.
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6e2b1ee845f45591a892d14caa0d126e981fb4b2ce71e70524580370ce4ce2c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338494"
---
# <a name="idebugreference2"></a>IDebugReference2
Bu arabirim, bir yığın çerçevesi özelliğine veya başka bir özelle ilgili bir başvuru temsil eder.

> [!NOTE]
> `IDebugReference2` , gelecekte kullanılmak üzere ayrılmıştır ve tüm yöntemleri de `E_NOTIMPL` dönüşletir.

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, belirli bir değere başvuru olduğunu temsil etmek için bu arabirimi uygulamaya almaktadır. Örneğin, değer bir ifade değerlendirmesinin sonucu olarak sayısal bir değer, belleği görüntülemek için kullanılan bir bellek bağlamı veya yazmayların ve değerlerinin listesi olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu [arabirimi almak için GetReference'ı](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) çağırma. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) ve [GetDerivedMostReference da](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugReference2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Bu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) açıklayan bir veri yapısı alır.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Bu başvuru değerini bir dizeden ayarlar.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Bu başvuru değerini başka bir başvurudan ayarlar.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Bu başvuruya yapılan başvuruların en küçüklerini numaralandır.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Bu başvuru için üst öğe alır.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Bu başvuru için en çok türetilmiş başvuru alır.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Bu başvuru için başvurulan bellek baytlarını alır.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Bu başvuru için bir bellek bağlamı alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Bu başvuru için bayt cinsinden boyutu alır.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Bu başvuru türünü ayarlar.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Bu başvuru başka bir başvuruyla karşılaştırıldığında.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu "özellik" kullanımı, bir sınıfın üye değişkeni anlamına gelen ile karıştırılmamalıdır, ancak bir böyle `IDebugReference2` bir varlığı temsil eder.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) bir özelliği temsil ederken, bir özelliğin başvurularını temsil ederken, genellikle hata ayıklaması yapılan programda bir `IDebugReference2` nesneye yapılan başvuru.

 Bir özellik ile başvuru arasındaki temel fark, bir özelliğin bir nesnenin adlandırılmış örneğine, başvuru ise adsız bir örneği ifade eder. Örneğin, bir özellik tarafından programın yığınında bir nesnesine `"a.b"` başvurabilirsiniz. Başka bir özellik ile aynı nesneye `"c.d"` başvurur. Bu özeliklere başvuru yapmak için bunun veya `"a.b"` `"c.d"` kapsamının içinde olması gerekir. Bu nesneye yapılan başvurular adsızdır; bu nesnenin belleği geçerli olduğu sürece nesnesine başvurulabilirsiniz.

 Arabirim `IDebugProperty2` adı, türü ve adresi olan bir değer olarak düşünebilirsiniz. Öte yandan , `IDebugReference2` türü ve adresi olarak düşünebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
