---
title: IDebugReference2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720269"
---
# <a name="idebugreference2"></a>IDebugReference2
Bu arabirim, yığın çerçevesi özelliğine veya başka bir özelliğe başvurur.

> [!NOTE]
> `IDebugReference2`gelecekteki kullanım için ayrılmıştır ve tüm `E_NOTIMPL`yöntemleri geri dönmelidir.

## <a name="syntax"></a>Sözdizimi

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, belirli bir değer türüne başvuruyu temsil etmek için bu arabirimi uygular. Örneğin, bir ifade değerlendirmesi, bellek görüntülemek için kullanılan bir bellek bağlamı veya kayıt listesi ve değerleri sonucunda değer sayısal bir değer olabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için [GetReference'ı](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) arayın. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) ve [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) da bu arabirimi döndürün.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugReference2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Bu başvuruyu açıklayan [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıyı alır.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Bu başvurunun değerini bir dizeden ayarlar.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Bu başvurunun değerini başka bir başvurudan ayarlar.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Bu referansın çocuklarını sayısal.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Bu başvurunun üst öğesini alır.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Bu başvurunun en çok türetilmiş referansını alır.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Bu başvurunun atıfta bulunduğu bellek baytlarını alır.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Bu başvuru için bir bellek bağlamı alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Bu referansın boyutunu baytolarak alır.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Bu başvuru türünü ayarlar.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Bu başvuruyla başka bir başvuruyla karşılaştırır.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> "Özellik" bu kullanımı bir sınıfın bir üye değişken anlamı ile `IDebugReference2` karıştırılmamalıdır, ancak bir tür bir varlık temsil edebilir.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) bir özelliği `IDebugReference2` temsil ederken, bir özellik için bir başvuru temsil ederken, genellikle programda bir nesneye bir başvuru debugged ediliyor.

 Bir özellik ve başvuru arasındaki temel fark, bir özelliğin nesnenin adlandırılmış örneğine başvurması, başvurunun ise advers bir örneğe başvurmasıdır. Örneğin, bir özellik, programın yığınındaki bir nesneye `"a.b"`'. Başka bir özellik aynı nesneye `"c.d"`'. Bu özellik atıfta yolu gerektirir `"a.b"` veya `"c.d"` kapsam içinde olmak. Aynı nesneye yapılan başvuru isimsizdir; nesne, söz konusu nesnenin belleği geçerli olduğu sürece adlandırılabilir.

 Arabirim, `IDebugProperty2` bir ad, tür ve adres içeren bir değer olarak düşünülebilir. Bir `IDebugReference2`, diğer taraftan, bir tür ve bir adres olarak düşünülebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
