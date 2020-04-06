---
title: IDebugBinder | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735963"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, sembolün geçerli değerini içeren bir bellek bağlamına veya nesneye bağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim ifade değerlendirmesini destekler ve hata ayıklama altyapısı (DE) tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim ifade değerlendirme sürecinde kullanılır ve genellikle [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)uygulamasında kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugBinder`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Bağla](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Simgenin geçerli değerini içeren bellek bağlamını veya nesneyi alır.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bir nesnenin çalışma zamanı türünü belirler.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Nesne konumunu veya bellek adresini bellek bağlamına dönüştürür.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|İşlev parametreleri oluşturmak için kullanılan bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi alır.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Bir değişkenin tam türünü alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, ayrışdırıcı ağaçlarda ifade değerlendiricisi tarafından kullanılan nesneleri döndürür. İfade değerlendiricisi, ifadedeki sembolleri kaynak kodundaki türü ve konumu açısından açıklayan [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)örneklerine dönüştürmek için sembol sağlayıcısını kullanarak ifadeyi ayrıştırır. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi, `IDebugField` nesneleri, bir sembol türünü bellekteki gerçek bir değere bağlayan veya bağlayan [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerine dönüştürür. Bu `IDebugObject` nesneler daha sonra değerlendirme için ayrışdırır ağaçta depolanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
