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
ms.openlocfilehash: cb94ceba197e0006dee98392df01f836c45692c9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726995"
---
# <a name="idebugreference2"></a>IDebugReference2
Bu arabirim, bir yığın çerçevesi özelliğine veya başka bir özelle ilgili bir başvuru temsil eder.

> [!NOTE]
> `IDebugReference2` gelecekteki kullanım için ayrılmıştır ve tüm yöntemleri tarafından getirilene kadar her yönteme sahip olması `E_NOTIMPL` gerekir.

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, belirli bir değere başvuru olduğunu temsil etmek için bu arabirimi uygulamaya almaktadır. Örneğin, değer bir ifade değerlendirmesinin sonucu olarak sayısal bir değer, belleği görüntülemek için kullanılan bir bellek bağlamı veya yazmayların ve değerlerinin listesi olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu [arabirimi almak için GetReference'ı](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) çağırma. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) ve [GetDerivedMostReference da](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
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

 Bir özellik ile başvuru arasındaki temel fark, bir özelliğin bir nesnenin adlandırılmış örneğine, başvuru ise adsız bir örneği ifade eder. Örneğin, bir özellik tarafından programın yığınında bir nesnesine `"a.b"` başvurabilirsiniz. Başka bir özellik ile aynı nesneye `"c.d"` başvurur. Bu özeliklere başvuru yapmak için bunun veya `"a.b"` `"c.d"` kapsamının içinde olması gerekir. Bu nesneye yapılan başvuru adsızdır; bu nesnenin belleği geçerli olduğu sürece nesnesine başvurulabilirsiniz.

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
